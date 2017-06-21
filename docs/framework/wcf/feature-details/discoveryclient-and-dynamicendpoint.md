---
title: "DiscoveryClient y DynamicEndpoint | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# DiscoveryClient y DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient> y <xref:System.ServiceModel.Discovery.DynamicEndpoint> son dos clases usadas en el lado cliente para buscar servicios.<xref:System.ServiceModel.Discovery.DiscoveryClient> le proporciona una lista de servicios que coinciden con un conjunto concreto de criterios y le permite conectarse a los servicios.<xref:System.ServiceModel.Discovery.DynamicEndpoint> realiza la misma operación y además, conecta automáticamente con uno de los servicios que se encontró.Cualquier extremo se puede convertir en <xref:System.ServiceModel.Discovery.DynamicEndpoint>, los criterios de búsqueda también se pueden agregar a través de la configuración. Por tanto, <xref:System.ServiceModel.Discovery.DynamicEndpoint> es útil si necesita la detección en su solución pero no desea modificar la lógica del cliente; solo necesita modificar los extremos.Por otra parte, <xref:System.ServiceModel.Discovery.DiscoveryClient> se puede usar para obtener un control más preciso sobre la operación de búsqueda.Más abajo, se elaboran los usos y ventajas de cada uno.  
  
## DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> define métodos Find sincrónicos y asincrónicos, así como eventos <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> y <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>.También define métodos Resolve sincrónicos y asincrónicos, así como un evento <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted>.Utilice los métodos <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> o <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> para buscar servicios.Ambos métodos toma una instancia <xref:System.ServiceModel.Discovery.FindCriteria> que le permite especificar los nombres de tipo de contrato, ámbitos, número máximo de resultados solicitados y reglas de coincidencia de ámbito.Los eventos <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> y <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> se pueden usar al llamar al método <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A>.<xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> se desencadena siempre que <xref:System.ServiceModel.Discovery.DiscoveryClient> recibe una respuesta de un servicio.Se puede utilizar para mostrar una barra de progreso que muestra el progreso de la operación de búsqueda.También se puede utilizar para intervenir en la búsqueda de respuestas a medida que se reciben.El evento <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> se desencadena cuando finaliza la operación de búsqueda.Esto puede pasar porque se haya recibido el número máximo de respuestas o si ha transcurrido <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>.Cuando la operación de búsqueda finaliza, los resultados se devuelven en una instancia <xref:System.ServiceModel.Discovery.FindResponse>.<xref:System.ServiceModel.Discovery.FindResponse> contiene una recopilación de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> que incluye las direcciones, los nombres del tipo de contrato, las extensiones, los URI de escucha y los ámbitos de los servicios coincidentes.A continuación, puede utilizar esta información para conectarse y llamar a uno de los servicios coincidentes.En el siguiente ejemplo, se muestra cómo llamar al método [the M:System.ServiceModel.Discovery.DiscoveryClient.Find\(System.ServiceModel.Discovery.FindCriteria\)](assetId:///the M:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)?qualifyHint=False&autoUpgrade=True) y utilizar los metadatos devueltos para llamar al servicio encontrado.Una ventaja de utilizar <xref:System.ServiceModel.Discovery.DiscoveryClient> es que puede almacenar en memoria caché la lista de extremos encontrados y usarlos en un momento posterior.Con esta memoria caché, puede crear una lógica personalizada para administrar diversas condiciones de error.  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
FindCriteria criteria = new FindCriteria(typeof(ICalculatorService));  
FindResponse fr = dc.Find(criteria);  
  
if (fr.Endpoints.Count > 0)  
{  
   EndpointAddress ep = fr.Endpoints[0].Address;  
   CalculatorServiceClient client = new CalculatorServiceClient();  
  
    // Connect to the discovered service endpoint  
   client.Endpoint.Address = endpointAddress;  
   Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
}  
else  
   Console.WriteLine(“No matching endpoints found”);  
  
```  
  
 En el siguiente ejemplo, se muestra cómo realizar una operación de búsqueda de forma asincrónica.  
  
```  
static void FindServiceAsync()  
{  
   DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());   
   dc.FindCompleted += new EventHandler<FindCompletedEventArgs>( discoveryClient_FindCompleted);  
   dc.FindProgressChanged += new EventHandler<FindProgressChangedEventArgs>(discoveryClient_FindProgressChanged);  
   dc.FindAsync(new FindCriteria(typeof(ICalculatorService)));   
}   
static void discoveryClient_FindProgressChanged(object sender, FindProgressChangedEventArgs e)  
{  
   Console.WriteLine("Found service at: " + e.EndpointDiscoveryMetadata.Address  
}   
  
static void discoveryClient_FindCompleted(object sender, FindCompletedEventArgs e)  
{    
      if (e.Result.Endpoints.Count > 0)  
            {  
                EndpointAddress ep = e.Result.Endpoints[0].Address;  
                CalculatorServiceClient client = new CalculatorServiceClient();  
  
                // Connect to the discovered service endpoint  
                client.Endpoint.Address = ep;  
                Console.WriteLine("Invoking CalculatorService at {0}", ep);  
  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
            }  
            else  
                Console.WriteLine("No matching endpoints found");  
  
        }  
  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la realización de llamadas de búsqueda asincrónicas, vea [Búsqueda asincrónica](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md).  
  
 Utilice los métodos <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> y <xref:System.ServiceModel.Discovery.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> para buscar un servicio basado en su dirección de extremo.Esto es útil cuando la dirección del extremo no es ninguna red direccionable.Los métodos Resolve toman una instancia de <xref:System.ServiceModel.Discovery.ResolveCriteria> que le permite especificar la dirección del extremo del servicio que está resolviendo, la duración máxima de la operación de resolución y un conjunto de extensiones.En el ejemplo siguiente, se muestra cómo utilizar el método <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> para resolver un servicio.  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
  
```  
  
## DynamicEndpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint> es un extremo estándar \([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Extremos estándar](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)\) que realiza la detección y selecciona automáticamente un servicio coincidente.Simplemente cree una clase <xref:System.ServiceModel.Discovery.DynamicEndpoint> pasando el contrato que se va a buscar y el enlace para usar y pasar la instancia <xref:System.ServiceModel.Discovery.DynamicEndpoint> al cliente de WCF.En el siguiente ejemplo, se muestra cómo crear y usar una clase <xref:System.ServiceModel.Discovery.DynamicEndpoint> para llamar al servicio de calculadora.La detección se realiza cada vez que se abre el cliente.Cualquier extremo definido en la configuración se puede convertir también en <xref:System.ServiceModel.Discovery.DynamicEndpoint> agregando el atributo `kind =”dynamicEndpoint”` al elemento de configuración del extremo.  
  
```  
  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
```  
  
## Vea también  
 [Detección con ámbitos](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)   
 [Búsqueda asincrónica](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)   
 [Básico](../../../../docs/framework/wcf/samples/basic-sample.md)