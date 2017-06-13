---
title: "Paramètres d’Extension de remise de Reporting Services | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
- XML Web service [Reporting Services], delivery extension settings
- Report Server Web service, delivery extension settings
- delivery [Reporting Services]
- network share delivery [Reporting Services]
- file share delivery [Reporting Services]
- e-mail [Reporting Services]
- mailing reports [Reporting Services]
- sharing reports
- extensions [Reporting Services], delivery
- mail [Reporting Services]
- Web service [Reporting Services], delivery extension settings
ms.assetid: 68c31a85-261c-4ec4-b8df-1f9842b46f8a
caps.latest.revision: 36
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 668c3d31af5f287d7d254c2dc666e20a5f6328fa
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="reporting-services-delivery-extension-settings"></a>Paramètres des extensions de remise de Reporting Services
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]inclut une extension de remise par messagerie et une extension de remise de partage de fichiers. La remise par messagerie permet d'envoyer un rapport à des utilisateurs individuels ou à des groupes par le biais de la messagerie électronique. La remise par partage de fichiers permet d'envoyer automatiquement des rapports rendus à un partage de votre réseau. Vous pouvez utiliser l'une ou l'autre de ces extensions de remise avec des abonnements standard ou des abonnements piloté par les données. Vous devez transmettre les paramètres de remise qui sont spécifiques au type d'extension de remise chaque fois que vous appelez les méthodes <xref:ReportService2010.ReportingService2010.CreateSubscription%2A>, <xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>, <xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A> et <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A>. Pour extraire par programme la liste des paramètres de remise, utilisez la méthode <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A>.  
  
> [!NOTE]  
>  Les paramètres d'extension de remise respectent la casse.  
  
## <a name="e-mail-delivery-settings"></a>Paramètres de remise par messagerie  
 Le tableau suivant répertorie les paramètres de remise par messagerie pour les abonnements qui utilisent la messagerie électronique du serveur de rapports.  
  
|Paramètre|Value|  
|-------------|-----------|  
|**À**|L’adresse de messagerie qui apparaît sur le **à** ligne du message électronique. Les adresses de messagerie multiples sont séparées par des points-virgules. Obligatoire.|  
|**CC**|L’adresse de messagerie qui apparaît sur le **Cc** ligne du message électronique. Les adresses de messagerie multiples sont séparées par des points-virgules. Ce paramètre est facultatif.|  
|**CCI**|L’adresse de messagerie qui apparaît sur le **Cci** ligne du message électronique. Les adresses de messagerie multiples sont séparées par des points-virgules. Ce paramètre est facultatif.|  
|**ReplyTo**|L’adresse de messagerie qui apparaît dans le **réponse** en-tête du message électronique. Il doit s'agir d'une adresse de messagerie unique. Ce paramètre est facultatif.|  
|**Inclure**|Valeur indiquant si le rapport doit être inclus dans la remise par messagerie. La valeur **true** indique que le rapport est remis dans le corps du message électronique.|  
|**RenderFormat**|Nom de l'extension de rendu à utiliser pour générer le rapport rendu. Ce nom doit correspondre à l'une des extensions de rendu visibles installées sur le serveur de rapports. Cette valeur est obligatoire si le **inclure** est défini sur une valeur de **true**.|  
|**Priorité**|Priorité avec laquelle le message électronique est envoyé. Les valeurs valides sont **faible**, **NORMAL**, et **haute**. La valeur par défaut est **NORMAL**.|  
|**Objet**|Texte figurant dans la ligne Objet du message électronique.|  
|**Commentaireaire**|Texte inclus dans le corps du message électronique.|  
|**IncludeLink**|Valeur qui indique si un lien vers le rapport doit être inclus dans le corps du message électronique.|  
  
## <a name="file-share-delivery-settings"></a>Paramètres de remise par partage de fichiers  
 Le tableau suivant répertorie les paramètres de remise par partage de fichiers pour les abonnements.  
  
|Paramètre|Valeur|  
|-------------|-----------|  
|**NOM DE FICHIER**|Nom du fichier qui est enregistré sur le disque.|  
|**FILEEXTN**|Indique si une extension de fichier doit être incluse pour le rapport rendu. La valeur est soit **true** ou **false**.|  
|**CHEMIN D’ACCÈS**|Chemin d'accès au dossier ou chemin d'accès au partage de fichiers UNC dans lequel enregistrer le rapport.|  
|**RENDER_FORMAT**|Format du rapport qui est enregistré sur le disque.|  
|**NOM D’UTILISATEUR**|Nom d'utilisateur requis pour accéder à la ressource réseau ou au disque.|  
|**MOT DE PASSE**|Mot de passe requis pour accéder à la ressource réseau ou au disque.|  
|**WRITEMODE**|Mode écriture à utiliser lors de l'accès au disque. Les valeurs valides sont **aucun**, **remplacer**, et **AutoIncrement**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations techniques de référence &#40;SSRS&#41;](../../../reporting-services/technical-reference-ssrs.md)   
 [Génération d’Applications à l’aide du Service Web et le .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
