---
title: 'Procédure : Déployer un élément de rapport personnalisé | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, deploying
ms.assetid: 80e97b0d-e355-4240-aebd-08cbc84089ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b41519ee6a6d31be33d92c8fbdf2ab503c93ec1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63265081"
---
# <a name="how-to-deploy-a-custom-report-item"></a>Procédure : Déployer un élément de rapport personnalisé
  Pour déployer un élément de rapport personnalisé dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous devez d'abord modifier les fichiers de configuration du serveur de rapports, puis copier les assemblys correspondant aux composants de conception et d'exécution dans les dossiers d'application appropriés, et ce à la fois pour le Concepteur de rapports et le serveur de rapports.  
  
### <a name="to-deploy-a-custom-report-item"></a>Pour déployer un élément de rapport personnalisé  
  
1.  Modifiez le fichier Rsreportdesigner.config afin de configurer les composants de conception et d'exécution de l'élément de rapport personnalisé à utiliser dans le concepteur. N'oubliez pas que l'entrée `ReportItemName` doit correspondre à l'attribut `CustomReportItemAttribute` utilisé dans la classe `CustomReportItemDesigner`. Exemple :  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    <ReportItemDesigner>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsDesigner, PolygonsDesigner" />  
    </ReportItemDesigner>  
    <ReportItemConverter>  
       <Converter Source="Chart" Target="Polygons" Type="PolygonsCRI.PolygonsConverter, PolygonsDesigner" />  
    </ReportItemConverter>  
    ```  
  
2.  Modifiez le fichier Rsreportserver.config pour inscrire le composant d'exécution de l'élément de rapport personnalisé. Exemple :  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    ```  
  
3.  Modifiez le fichier Rssrvpolicy.config pour ajouter un `CodeGroup` octroyant les autorisations adéquates à l'élément de rapport personnalisé. Exemple :  
  
    ```  
    <CodeGroup   
       class="UnionCodeGroup"   
       version="1"   
       PermissionSetName="FullTrust"  
       Description="This code group grants MyCustomReportItem.dll FullTrust permission. ">  
       <IMembershipCondition   
          class="UrlMembershipCondition"  
          version="1"  
       Url="C:\Program Files\Microsoft SQL Server\ MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin\MyCustomReportItem.dll" />  
    </CodeGroup>  
    ```  
  
4.  Copiez le fichier DLL correspondant au composant d'exécution de l'élément de rapport personnalisé dans les répertoires bin du serveur de rapports qui se trouvent à l'emplacement suivant : %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies et \Program Files\Microsoft SQL Server\MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin.  
  
5.  Copiez le fichier DLL correspondant au composant de conception de l'élément de rapport personnalisé dans le répertoire PrivateAssemblies, lequel se trouve à l'emplacement suivant : %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de configuration de Reporting Services](../report-server/reporting-services-configuration-files.md)   
 [Bibliothèques de classes d'éléments de rapports personnalisés](custom-report-item-class-libraries.md)  
  
  
