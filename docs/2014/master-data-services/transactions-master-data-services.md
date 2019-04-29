---
title: Transactions (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Master Data Services], about transactions
- transactions [Master Data Services]
ms.assetid: 4cd2fa6f-9c76-4b7a-ae18-d4e5fd2f03f5
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: b309669027da801681c1386abe604fce2f915f3d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923248"
---
# <a name="transactions-master-data-services"></a>Transactions (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], une transaction est enregistrée à chaque fois qu'une action est effectuée sur un membre. Les transactions peuvent être affichées par tous les utilisateurs et être inversées par les administrateurs. Les transactions affichent la date, l'heure et l'utilisateur qui a effectué l'action, ainsi que d'autres détails. Les utilisateurs peuvent ajouter une annotation à une transaction, pour indiquer pourquoi une transaction a eu lieu.  
  
## <a name="when-transaction-are-recorded"></a>Critères d'enregistrement des transactions  
 Des transactions sont enregistrées lorsque des membres :  
  
-   sont créés, supprimés ou réactivés ;  
  
-   ont des valeurs d'attribut modifiées ;  
  
-   sont inclus dans une hiérarchie.  
  
 Les transactions ne sont pas enregistrées lorsque les règles d'entreprise modifient des valeurs d'attribut.  
  
## <a name="view-and-manage-transactions"></a>Afficher et gérer des transactions  
 Dans la zone fonctionnelle **Explorateur** , vous pouvez afficher et annoter les transactions (leur ajouter des commentaires) que vous avez effectuées.  
  
 Dans la zone fonctionnelle **Gestion des versions** , les administrateurs peuvent consulter toutes les transactions de tous les utilisateurs pour les modèles auxquels ils ont accès, et inverser l'une quelconque de ces transactions.  
  
> [!NOTE]  
>  Les administrateurs peuvent afficher toutes les transactions pour tous les utilisateurs tant qu’ils n’ont pas le niveau d’autorisation de lecture seule appliqué dans la zone fonctionnelle **Gestion des versions**. Par exemple, si le niveau d’autorisation de lecture seule et de mise à jour est défini pour l’administrateur, celui-ci ne peut pas voir les autres transactions utilisateur, car l’autorisation de lecture seule est prioritaire sur l’autorisation de mise à jour.

## <a name="system-settings"></a>Paramètres système  
 Il existe un paramètre dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] qui détermine si les transactions sont enregistrées ou non lors de l'organisation des enregistrements. Ce paramètre affecte SQL Server 2008 R2 uniquement. Vous pouvez ajuster ce paramètre dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] ou directement dans la table Paramètres système de la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Pour plus d’informations, consultez [Paramètres système &#40;Master Data Services&#41;](system-settings-master-data-services.md).  
  
 Lors de l'importation de données dans cette version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], vous pouvez spécifier s'il faut enregistrer les transactions lors de l'initialisation de la procédure stockée. Pour plus d’informations, consultez [Procédure stockée de mise en lots &#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).  
  
## <a name="concurrency"></a>Accès concurrentiel  
 Si une valeur d'entité spécifique est affichée simultanément dans plusieurs sessions de l'Explorateur, les modifications simultanées d'une même valeur sont possibles. Les modifications simultanées ne sont pas détectées automatiquement par MDS. Cela peut se produire lorsque plusieurs utilisateurs utilisent plusieurs sessions de l'explorateur MDS dans le navigateur Web, par exemple sur plusieurs ordinateurs, sous plusieurs onglets de navigateur ou dans plusieurs fenêtres, ou avec plusieurs comptes utilisateur.  
  
 Plusieurs utilisateurs peuvent mettre à jour les mêmes valeurs d'entité sans erreur malgré les transactions activées. En général, la dernière modification de la valeur dans un même intervalle de temps prévaut. Les conflits de modifications en double peuvent être observés dans l'historique des transactions et peuvent être corrigés manuellement par l'administrateur. L'historique des transactions affiche les transactions individuelles pour **Valeur précédente** et **Nouvelle valeur** pour l'attribut en question dans chaque session, mais ne corrige pas automatiquement le conflit lorsque plusieurs **Nouvelles valeurs** existent pour la même valeur de départ.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Annuler une action en inversant une transaction (administrateurs uniquement)|[Inverser une transaction &#40;Master Data Services&#41;](../../2014/master-data-services/reverse-a-transaction-master-data-services.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Administrateurs &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)  
  
-   [Annotations &#40;Master Data Services&#41;](../../2014/master-data-services/annotations-master-data-services.md)  
  
  
