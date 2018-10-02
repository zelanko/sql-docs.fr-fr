---
title: rsServerConfigurationError - Erreur Reporting Services | Microsoft Docs
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: troubleshooting
ms.topic: conceptual
helpviewer_keywords:
- rsServerConfigurationError
ms.assetid: 0913afc2-34b4-4713-b570-cfd5718975ac
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a03e276df871e7949ac01b7e0f1698dafcb36bf2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47793083"
---
# <a name="rsserverconfigurationerror---reporting-services-error"></a>rsServerConfigurationError - Erreur Reporting Services
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|rsServerConfiguration|  
|Source de l'événement|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Composant|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Texte du message|Le serveur de rapports a rencontré une erreur de configuration.|  
  
## <a name="explanation"></a>Explication  
 Ceci est une erreur à usage général qui se produit lorsque le serveur de rapports ou un outil de création de rapport a des paramètres de configuration non valides. L'erreur est accompagnée habituellement d'un second message qui indique la cause réelle de l'erreur.  
  
 La liste suivante résume les causes possibles :  
  
-   Le fichier RSReportServer.config ou RSReportDesigner.config est introuvable ou illisible.  
  
-   Des éléments XML dans l'un des fichiers de configuration sont manquants ou non valides.  
  
-   Les valeurs d'un ou de plusieurs éléments XML sont manquantes ou non valides.  
  
-   Les paramètres du Registre ne sont pas valides.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Si cette erreur a commencé à se produire après que vous avez modifié manuellement un fichier de configuration, supprimez vos modifications et entrez la valeur précédente, ou restaurez une version précédente si vous disposez d'une sauvegarde.  
  
 Pour examiner des informations de message d’erreur supplémentaires qui accompagnent l’erreur **rsServerConfiguration**, examinez les fichiers journaux des traces du serveur de rapports, qui se trouvent dans \Microsoft SQL Server\MSRS12.\<nom_instance>\Reporting Services\LogFiles. Pour plus d’informations, consultez [Fichiers journaux et sources de Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md).  
  
## <a name="internal-only"></a>Interne uniquement  
  
## <a name="see-also"></a> Voir aussi  
 [Fichiers de configuration Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Modifier un fichier de configuration Reporting Services &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)  
  
  
