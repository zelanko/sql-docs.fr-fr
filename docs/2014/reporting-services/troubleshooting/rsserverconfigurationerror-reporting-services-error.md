---
title: rsServerConfigurationError - Erreur Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- rsServerConfigurationError
ms.assetid: 0913afc2-34b4-4713-b570-cfd5718975ac
caps.latest.revision: 11
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 49183fb1ff712ee3d0be8cd76d99492fcc9a93d1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152761"
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
  
 Pour passer en revue les informations de message d’erreur supplémentaires qui accompagnent le `rsServerConfiguration` erreur, examinez les rapport trace fichiers journaux du serveur qui se trouvent dans \Microsoft SQL Server\MSRS12.\< InstanceName > \Reporting Services\LogFiles. Pour plus d’informations, consultez [Fichiers journaux et sources de Reporting Services](../report-server/reporting-services-log-files-and-sources.md).  
  
## <a name="internal-only"></a>Interne uniquement  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de configuration de Reporting Services](../report-server/reporting-services-configuration-files.md)   
 [Modifier un fichier de configuration Reporting Services &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)  
  
  