---
title: rsInternalError - Erreur Reporting Services | Microsoft Docs
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
- rsInternalError
ms.assetid: 52613d52-fc78-4870-93f0-7d393ab9c335
caps.latest.revision: 21
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 84b2079bbc588447991f767f74a216eafd9cac46
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041532"
---
# <a name="rsinternalerror---reporting-services-error"></a>rsInternalError - Erreur Reporting Services
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|rsInternalError|  
|Source de l'événement|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Composant|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Texte du message|Une erreur interne s'est produite sur le serveur de rapports. Consultez le journal des erreurs pour plus d'informations.|  
  
## <a name="explanation"></a>Explication  
 Il s'agit d'un message d'erreur générique qui est souvent suivi par un autre message plus descriptif fournissant des informations détaillées.  
  
 Les erreurs internes sont rares. Si vous recevez ce message, des informations supplémentaires sont disponibles dans les journaux des traces du serveur de rapports. En outre, si vous êtes connecté en tant qu'administrateur local sur l'ordinateur sur lequel l'erreur s'est produite, vous pouvez afficher la pile des appels pour avoir accès à des informations supplémentaires.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour déterminer la cause spécifique de ce message, passez en revue les fichiers journaux du serveur de rapports qui se trouvent dans le dossier \Microsoft SQL Server\MSRS12.\<nom_instance>\Reporting Services\LogFiles. Pour plus d’informations, consultez [Fichiers journaux et sources de Reporting Services](../report-server/reporting-services-log-files-and-sources.md).  
  
 Pour afficher la pile des appels, cliquez avec le bouton droit sur la page sur laquelle l’erreur s’est produite et pointez sur **Afficher la source**. La consultation de la pile des appels requiert des autorisations d'administrateur sur l'ordinateur où l'erreur s'est produite.  
  
 Si aucune information supplémentaire n'est disponible, vous pouvez réessayer votre demande.  
  
## <a name="internal-only"></a>Interne uniquement  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer et arrêter le service du serveur de rapports](../report-server/start-and-stop-the-report-server-service.md)  
  
  