---
title: punto de conexión personalizado de metadatos seguros
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2baa99ddaf5de60407b233b5a6ea013ad87401f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="custom-secure-metadata-endpoint"></a>punto de conexión personalizado de metadatos seguros
Este ejemplo muestra cómo implementar un servicio con un punto de conexión seguro de metadatos que utiliza uno de los enlaces de intercambio de metadatos no y cómo configurar [la herramienta de utilidad de metadatos de ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) o los clientes para capturar el metadatos de un punto de conexión de metadatos. Hay dos enlaces proporcionados por el sistema disponibles para exponer puntos de conexión de metadatos: mexHttpBinding y mexHttpsBinding. mexHttpBinding se usa para exponer un punto de conexión de metadatos sobre HTTP de una manera no segura. mexHttpsBinding se usa para exponer un punto de conexión de metadatos sobre HTTPS de una manera no segura. En este ejemplo se muestra cómo exponer un extremo de metadatos seguro mediante el objeto <xref:System.ServiceModel.WSHttpBinding>. Desearía hacer esto cuando desee cambiar la configuración de seguridad en el enlace, pero no desee usar HTTPS. Si utiliza mexHttpsBinding, su extremo de metadatos será seguro, pero no hay ninguna manera de modificar la configuración del enlace.  
  
> [!NOTE]
>  El procedimiento de instalación y las instrucciones de compilación de este ejemplo se encuentran al final de este tema.  
  
## <a name="service"></a>web de Office  
 El servicio en este ejemplo tiene dos extremos. El extremo de la aplicación sirve el contrato `ICalculator` en `WSHttpBinding` con `ReliableSession` habilitados y seguridad `Message` utilizando certificados. El extremo de metadatos también utiliza `WSHttpBinding`, con la misma configuración de seguridad pero sin `ReliableSession`. Aquí está la configuración pertinente:  
  
```xml  
<services>   
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- use base address provided by host -->  
     <endpoint address=""  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding2"  
       contract="Microsoft.ServiceModel.Samples.ICalculator" />  
     <endpoint address="mex"  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding1"  
       contract="IMetadataExchange" />  
     </service>  
 </services>  
 <bindings>  
   <wsHttpBinding>  
     <binding name="Binding1">  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
     <binding name="Binding2">  
       <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
   </wsHttpBinding>  
 </bindings>  
```  
  
 En muchos de los otros ejemplos, el extremo de metadatos utiliza el `mexHttpBinding`predeterminado, que no es seguro. Aquí los metadatos se protegen utilizando `WSHttpBinding` con seguridad `Message`. Para que los clientes de los metadatos recuperen estos metadatos, se deben configurar con un enlace correspondiente. Este ejemplo muestra dos clientes de este tipo.  
  
 El primer cliente utiliza Svcutil.exe para capturar los metadatos y generar en tiempo de diseño código y configuración de cliente. Dado que el servicio utiliza un enlace no predeterminado para los metadatos, se debe configurar la herramienta Svcutil.exe específicamente para que pueda recibir los metadatos del servicio utilizando ese enlace.  
  
 El segundo cliente utiliza `MetadataResolver` para capturar dinámicamente los metadatos para un contrato conocido y a continuación, invocar las operaciones en el cliente generado dinámicamente.  
  
## <a name="svcutil-client"></a>Cliente de Svcutil  
 Al utilizar el enlace predeterminado para hospedar su extremo `IMetadataExchange`, puede ejecutar Svcutil.exe con la dirección de ese extremo:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 y funciona. Pero en este ejemplo, el servidor utiliza un extremo no predeterminado para hospedar los metadatos. Así que deben indicar a Svcutil.exe que utilice el enlace correcto. Esto se puede hacer utilizando un archivo Svcutil.exe.config.  
  
 El archivo Svcutil.exe.config se parece un archivo de configuración de cliente normal. Los únicos aspectos raros son el nombre de punto de conexión del cliente y su contrato:  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 El nombre de extremo debe ser el nombre del esquema de la dirección donde se hospedan los metadatos y el contrato del extremo debe ser `IMetadataExchange`. Así, cuando Svcutil.exe se ejecuta con una línea de comandos como la siguiente:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 busca el extremo denominado "http" y `IMetadataExchange` del contrato para configurar el enlace y comportamiento del intercambio de la comunicación con el extremo de metadatos. El resto del archivo Svcutil.exe.config en el ejemplo especifica las credenciales de comportamiento y configuración de enlace para hacer que coincida con la configuración del servidor del extremo de metadatos.  
  
 Para que Svcutil.exe recoja la configuración en Svcutil.exe.config, Svcutil.exe debe estar en el mismo directorio que el archivo de configuración. Como resultado, debe copiar Svcutil.exe de su ubicación de la instalación en el directorio que contiene el archivo Svcutil.exe.config. Entonces, desde ese directorio, ejecute el siguiente comando:  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 El interlineado ". \\"garantiza que se ejecuta la copia de Svcutil.exe en este directorio (el que tiene el Svcutil.exe.config correspondiente).  
  
## <a name="metadataresolver-client"></a>Cliente de MetadataResolver  
 Si el cliente conoce el contrato y cómo hablar en tiempo de diseño con los metadatos, el cliente puede averiguar dinámicamente el enlace y dirección de los extremos de la aplicación utilizando `MetadataResolver`. Este cliente de ejemplo demuestra esto mostrando cómo configurar el enlace y las credenciales utilizadas por `MetadataResolver` creando y configurando `MetadataExchangeClient`.  
  
 El mismo enlace e información del certificado que aparecieron en Svcutil.exe.config se pueden especificar imperiosamente en `MetadataExchangeClient`:  
  
```  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.    CertificateValidationMode =    X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 Con `mexClient` configurado, podemos enumerar los contratos en los que estamos interesados y utilizar `MetadataResolver` para capturar una lista de extremos con esos contratos:  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Finalmente, podemos utilizar la información de esos extremos para inicializar el enlace y la dirección de `ChannelFactory` utilizadas para crear los canales para comunicarse con los extremos de la aplicación.  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 El punto clave de este cliente de ejemplo es mostrar eso, si está utilizando `MetadataResolver`, y debe especificar enlaces personalizados o comportamientos para la comunicación de intercambio de metadatos, puede utilizar `MetadataExchangeClient` para especificar esos valores personalizados.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Para configurar y compilar el ejemplo  
  
1.  Asegúrese de que ha llevado a cabo la [procedimiento de instalación de un solo uso para los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar la solución, siga las instrucciones que aparecen en [compilar los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Para ejecutar el ejemplo en el mismo equipo  
  
1.  Ejecute Setup.bat desde la carpeta de instalación del ejemplo. De esta forma, se instalan todos los certificados necesarios para ejecutar el ejemplo. Tenga en cuenta que Setup.bat utiliza la herramienta FindPrivateKey.exe, que está instalada, ejecute setupCertTool.bat desde [procedimiento de instalación de un solo uso para los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Ejecutar la aplicación cliente desde \MetadataResolverClient\bin o \SvcutilClient\bin. La actividad del cliente se muestra en la aplicación de consola del cliente.  
  
3.  Si el cliente y el servicio no se pueden comunicar, consulte [sugerencias de solución de problemas de](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
4.  Quite los certificados ejecutando Cleanup.bat cuando haya finalizado con el ejemplo. Otros ejemplos de seguridad usan los mismos certificados.  
  
#### <a name="to-run-the-sample-across-machines"></a>Para ejecutar el ejemplo en los equipos  
  
1.  En el servidor, ejecute `setup.bat service`. Ejecuta `setup.bat` con el `service` argumento crea un certificado de servicio con el nombre de dominio completo de la máquina y exporta el certificado de servicio a un archivo denominado Service.cer.  
  
2.  En el servidor, edite Web.config para reflejar el nuevo nombre del certificado. Es decir, cambiar la `findValue` de atributo en el [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) elemento en el nombre de dominio completo de la máquina.  
  
3.  Copie el archivo Service.cer del directorio de servicio al directorio del cliente en el equipo cliente.  
  
4.  En el cliente, ejecute `setup.bat client`. Ejecuta `setup.bat` con el `client` argumento crea un certificado de cliente denominado Client.com y exporta el certificado de cliente a un archivo denominado Client.cer.  
  
5.  En el archivo App.config de `MetadataResolverClient` en el equipo cliente, cambie el valor de la dirección del extremo mex para que coincida con la nueva dirección de su servicio. Para hacerlo, reemplace el host local con el nombre de dominio completo del servidor. Cambie también la cadena "localhost" en el archivo metadataResolverClient.cs por el nuevo nombre del certificado del servicio (el nombre de dominio completo del servidor). Haga lo mismo para App.config en el proyecto SvcutilClient.  
  
6.  Copie el archivo Client.cer del directorio del cliente en el directorio del servicio en el servidor.  
  
7.  En el cliente, ejecute `ImportServiceCert.bat`. Así se importa el certificado del servicio del archivo Service.cer en el almacén CurrentUser - TrustedPeople.  
  
8.  En el servidor, ejecute `ImportClientCert.bat`. De esta manera se importa el certificado de cliente del archivo Client.cer en el almacén LocalMachine - TrustedPeople.  
  
9. En el equipo del servicio, compile el proyecto de servicio en Visual Studio y seleccione la página de ayuda en un explorador web para comprobar que se está ejecutando.  
  
10. En el equipo cliente, ejecute MetadataResolverClient o SvcutilClient desde VS.  
  
    1.  Si el cliente y el servicio no se pueden comunicar, consulte [sugerencias de solución de problemas de](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Para realizar una limpieza después de ejecutar el ejemplo  
  
-   Ejecute Cleanup.bat en la carpeta de ejemplos cuando haya terminado de ejecutar el ejemplo.  
  
    > [!NOTE]
    >  Este script no quita los certificados del servicio en un cliente cuando se ejecuta este ejemplo en los equipos. Si ha ejecutado ejemplos de Windows Communication Foundation (WCF) que usan certificados en los equipos, asegúrese de borrar los certificados de servicio que se hayan instalado en el almacén CurrentUser - TrustedPeople. Para ello, utilice el siguiente comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Por ejemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si este directorio no existe, vaya a [Windows Communication Foundation (WCF) y ejemplos de Windows Workflow Foundation (WF) para .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos. Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
  
## <a name="see-also"></a>Vea también
