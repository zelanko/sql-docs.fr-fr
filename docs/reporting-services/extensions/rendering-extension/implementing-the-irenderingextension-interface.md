---
title: "Implémentation de l’Interface IRenderingExtension | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- IRenderingExtension interface
- rendering extensions [Reporting Services], IRenderingExtension interface
ms.assetid: 74b2f2b7-6796-42da-ab7d-b05891ad4001
caps.latest.revision: 43
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 60eac755180faaba012c7fbd14001fcb66a37975
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="implementing-the-irenderingextension-interface"></a>Implémentation de l'interface IRenderingExtension 
  L'extension de rendu prend les résultats d'une définition de rapport qui est combinée aux données réelles et restitue les données résultantes dans un format utilisable. La transformation de la combinaison des données et de la mise en forme s'effectue par le biais d'une classe CLR (Common Language Runtime) qui implémente <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension>. Cela transforme le modèle objet en un format de sortie qui est consommable par une visionneuse, une imprimante ou une autre cible de sortie.  
  
 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> a trois méthodes qui doivent être codées :  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> : effectue le rendu du rapport.  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> : effectue le rendu d'un flux spécifique à partir du rapport.  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> :  obtient des informations supplémentaires, telles que des icônes, nécessaires pour le rapport.  
  
 Ces méthodes sont traitées en détail dans les sections suivantes.  
  
## <a name="render-method"></a>Méthode Render  
 La méthode <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> contient des arguments qui représentent les objets suivants :  
  
-   Le *rapport* que vous souhaitez restituer. Cet objet contient des informations sur les propriétés, les données et la disposition du rapport. Le rapport est la racine de l'arborescence du modèle objet de rapport.  
  
-   Le *ServerParameters* qui contiennent l’objet de dictionnaire de chaînes avec les paramètres du serveur de rapports, le cas échéant.  
  
-   Le *deviceInfo* paramètre contenant les paramètres du périphérique. Pour plus d’informations, consultez [en passant des paramètres d’informations de périphérique aux Extensions de rendu](../../../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
-   Le *clientCapabilities* paramètre qui contient un <xref:System.Collections.Specialized.NameValueCollection> objet dictionnaire qui comporte des informations sur le client pour lequel vous effectuez un rendu.  
  
-   Le *RenderProperties* qui contient des informations sur le résultat de rendu.  
  
-   Le *createAndRegisterStream* est une fonction de délégué à appeler pour obtenir un flux de données de rendu.  
  
### <a name="deviceinfo-parameter"></a>Paramètre deviceInfo  
 Le *deviceInfo* paramètre contient les paramètres de rendu, pas les paramètres de rapport. Ces paramètres de rendu sont passés à l'extension de rendu. Le *deviceInfo* valeurs sont converties en un <xref:System.Collections.Specialized.NameValueCollection> objet par le serveur de rapports. Les éléments dans le *deviceInfo* paramètre sont traitées comme valeurs pas la casse. Si la demande de rendu résulte d’URL d’accès, les paramètres d’URL sous la forme `rc:key=value` sont convertis en paires de clé/valeur le *deviceInfo* objet dictionnaire. Le code de détection du navigateur fournit également les éléments suivants dans le *clientCapabilities* dictionnaire : EcmaScriptVersion, JavaScript, MajorVersion, MinorVersion, Win32, Type et AcceptLanguage. Toute paire de nom/valeur le *deviceInfo* paramètre n’est pas compris par l’extension de rendu est ignorée. L'exemple de code suivant montre un exemple de méthode <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> qui extrait des icônes :  
  
```csharp  
public void GetRenderingResource (CreateStream createStreamCallback, NameValueCollection deviceInfo)  
{  
    string[] iconTagValues = deviceInfo.GetValues("Icon");  
    if ((iconTagValues != null) && (iconTagValues.Length > 0) )  
    {  
        // Create a stream to output to.  
        Stream outputStream = createStreamCallback(m_iconResourceName, "gif", null, "image/gif", false);  
        // Get the GIF image for one of the buttons on the toolbar  
        Image requiredImage = (Image) m_resourcemanager.GetObject(m_iconResourceName  
        // Write the image to the output stream  
        requiredImage.Save(outputStream, requiredImage.RawFormat);  
    }  
    return;  
}  
```  
  
## <a name="renderstream-method"></a>Méthode RenderStream  
 La méthode <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> restitue un flux particulier à partir du rapport. Tous les flux sont créés pendant l'appel <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> initial, mais les flux ne sont pas renvoyés initialement au client. Cette méthode est utilisée pour des flux secondaires (par exemple, des images dans le rendu HTML) ou des pages supplémentaires d'une extension de rendu multi-page (par exemple, Image/EMF).  
  
## <a name="getrenderingresource-method"></a>Méthode GetRenderingResource  
 La méthode <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> extrait les informations sans exécuter un rendu entier du rapport. Il arrive que le rapport requière des informations qui ne nécessitent pas le rendu du rapport lui-même. Par exemple, si vous avez besoin de l’icône associée à l’extension de rendu, utilisez la *deviceInfo* paramètre contenant la balise unique  **\<icône >**. Utilisez, dans ce cas, la méthode <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une Extension de rendu](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [Vue d'ensemble des extensions de rendu](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)  
  
  

