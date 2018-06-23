---
title: Utilitaires d’invite de commandes du serveur de rapports (SSRS) | Microsoft Docs
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
- rsconfig utility
- components [Reporting Services], command line utilities
- rs utility
- command prompt utilities [Reporting Services]
- rskeymgmt utility
ms.assetid: 68f2f9f4-f894-40ff-a71c-f9756bf4b68c
caps.latest.revision: 48
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 2aec66be072eec35cf36d2b1c418b7dcecfd337b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153391"
---
# <a name="report-server-command-prompt-utilities-ssrs"></a>Utilitaires d'invite de commandes du serveur de rapports (SSRS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] comprend plusieurs utilitaires de ligne de commande qui permettent d’administrer un serveur de rapports. Ces utilitaires sont installés automatiquement lorsque vous installez un serveur de rapports.  
  
|Nom   |Fichier de commandes|Mode de déploiement pris en charge|Description|  
|----------|------------------|-------------------------------|-----------------|  
|Utilitaire RSS|rs.exe|Mode natif et mode SharePoint. La version [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] inclut la prise en charge du mode SharePoint.|[L’utilitaire rs.exe](rs-exe-utility-ssrs.md) est un hôte de script que vous pouvez utiliser pour réaliser des opérations contenant des scripts. Par son intermédiaire, vous exécutez des scripts [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] pour publier des rapports, créer des éléments dans une base de données de serveur de rapports, copier des données entre des bases de données de serveurs de rapports, etc. Pour en savoir plus sur l’utilisation de scripts permettant d’administrer un serveur, consultez [Écrire des scripts pour les tâches d’administration et de déploiement](script-deployment-and-administrative-tasks.md).|  
|Applets de commande Powershell||SharePoint uniquement|Pour obtenir la liste des applets de commande powershell, consultez [applets de commande PowerShell pour Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md).|  
|rsconfig (utilitaire)|rsconfig.exe|Natif uniquement|Le [utilitaire rsconfig](rsconfig-utility-ssrs.md) est utilisé pour configurer et gérer une connexion de serveur de rapports à la base de données du serveur de rapports. mais aussi à définir un compte d'utilisateur pour le traitement des rapports autonomes. Pour plus d’informations, consultez [Serveur de rapports Reporting Services &#40;mode natif&#41;](../report-server/reporting-services-report-server-native-mode.md). Pour en savoir plus sur la configuration de la connexion, consultez [Configurer une connexion à la base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).|  
|Utilitaire Rskeymgmt|rskeymgmt.exe|Natif uniquement|Le [utilitaire rskeymgmt](rskeymgmt-utility-ssrs.md) est un outil de gestion de clés de chiffrement. Utilisez-le pour sauvegarder, appliquer, recréer et supprimer des clés symétriques. Cet outil sert également à attacher une instance de serveur de rapports à une base de données de serveur de rapports partagée. Rskeymgmt est utile dans les opérations de récupération de base de données. Réutilisez une base de données dans une nouvelle installation en appliquant un exemplaire sauvegardé de clé symétrique. Si les clés ne peuvent pas être récupérées, cet outil permet de supprimer le contenu chiffré dont vous ne vous servez plus. Pour en savoir plus sur la gestion des clés et le stockage des données confidentielles, consultez [Stocker des données chiffrées du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) et [Configurer et gérer des clés de chiffrement &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md).|  
  
> [!NOTE]  
>  Si vous préférez utiliser un outil qui a une interface utilisateur graphique, vous pouvez utiliser le Gestionnaire de Configuration de Reporting Services au lieu de `rsconfig` et `rskeymgmt`.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de Configuration de Reporting Services &#40;en Mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Outils de Reporting Services](reporting-services-tools.md)   
 [Serveur de rapports Reporting Services &#40;mode natif&#41;](../report-server/reporting-services-report-server-native-mode.md)  
  
  