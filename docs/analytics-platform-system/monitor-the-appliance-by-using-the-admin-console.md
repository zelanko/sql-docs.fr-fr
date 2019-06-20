---
title: Moniteur avec la Console d’administration - Analytique Platform System | Microsoft Docs
description: Pour le système de plateforme d’Analytique, la Console d’administration est une application web qui met en évidence les informations d’intégrité, état et les performances de l’appliance. Les utilisateurs se connecter à la Console d’administration via un navigateur internet.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d094f809052222238806e679e38c6578422fd9aa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63027547"
---
# <a name="monitor-the-appliance-with-the-admin-console---analytics-platform-system"></a>Surveiller l’appliance avec la Console d’administration - Analytique Platform System
La Console d’administration est une application web de SQL Server PDW qui met en évidence les informations d’intégrité, état et les performances de l’appliance. Les utilisateurs se connecter à la Console d’administration d’Internet Explorer.  
  
## <a name="About"></a>Sur la Console d’administration  
![Accueil Console des appliances](./media/monitor-the-appliance-by-using-the-admin-console/SQL_Server_PDW_AdminConsol_ApplHome.png "SQL_Server_PDW_AdminConsol_ApplHome")  
  
**Appliance**  
Dossier de base  
Fournit un résumé rapide de l’état de l’appliance.  
  
Contrôle d’intégrité  
Affiche la topologie d’appliances avec indicateurs montrant l’intégrité de chaque composant surveillé dans chaque nœud. Vous permet d’afficher l’état actuel des nœuds individuels et les propriétés des composants du nœud.  
  
Affiche les alertes matérielles et logicielles.  
  
Analyseur de performances  
Affiche des graphiques d’analyse de performances.  
  
**Parallel Data Warehouse**  
Dossier de base  
Fournit un résumé rapide de l’état PDW.  
  
Sessions  
Affiche les sessions utilisateur actives PDW. Cela peut vous aider pour la surveillance des conflits de ressources.  
  
Requêtes  
Affiche une liste de requêtes en cours d’exécution et récemment terminés. Il affiche les erreurs associées, le cas échéant. Fournit également la possibilité d’afficher les détails des requête d’exécution plan et le nœud d’exécution d’informations.  
  
Charges  
Affiche de charger les plans, l’état actuel de la charge PDW et les erreurs associées, le cas échéant.  
  
Sauvegardes/restaurations  
Affiche le journal de PDW sauvegarde et de restauration.  
  
Contrôle d’intégrité  
Affiche la topologie PDW avec indicateurs montrant l’intégrité de chaque composant surveillé dans chaque nœud. Vous permet d’afficher l’état actuel des nœuds individuels et les propriétés des composants du nœud.  
  
Affiche les alertes matérielles et logicielles.  
  
Ressources  
Affiche une liste des verrous de ressources PDW et leur état actuel.  
  
Stockage  
Résume l’utilisation du stockage PDW.  
  
Analyseur de performances  
Affiche des graphiques de moniteur de performances PDW.  
 
> [!NOTE]  
> La console d’administration a une résolution d’écran de 1024 x 768. La console d’administration affiche mieux avec une résolution d’écran de 1280 X 1024 ou plus.  
  
## <a name="Connect"></a>Se connecter à la Console d’administration  
Pour vous connecter à la Console d’administration requiert :  
  
-   Au moins Internet Explorer version 10.  
  
-   Autorisations d’accès de la Console d’administration. <!-- MISSING LINKS See [Grant Permissions to Use the Admin Console &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-use-the-admin-console-sql-server-pdw.md).  -->  
  
-   L’adresse IP du cluster de nœud de contrôle.  Obtenir auprès de votre administrateur SQL Server PDW.  
  
Pour vous connecter à la Console d’administration, utilisez Internet Explorer et https pour accéder à l’adresse IP du cluster de nœud de contrôle. Par exemple, si l’adresse IP du cluster de nœud de contrôle est `10.192.63.102`, entrez `https://10.192.63.102` dans la barre d’adresse de votre navigateur. Le premier écran demandera votre **connexion** et **mot de passe**. Fournir soit un compte de connexion de l’authentification SQL Server et mot de passe, ou une connexion via l’authentification Windows et mot de passe Windows. Si vous utilisez une connexion d’authentification de Windows, la Console d’administration utilisera l’emprunt d’identité.  
  
## <a name="RelatedTasks"></a>Tâches de la Console d’administration  
La Console d’administration fournit la capacité à surveiller les éléments suivants :  
  
|||  
|-|-|  
|**Type d’informations**|**Accès dans la Console d’administration**|  
|État global de l’appliance|Cliquez sur **Appliance état** dans le menu supérieur, ou **accueil**.|  
|Alertes|Cliquez sur **alertes**. Pour plus d’informations, consultez [présentation des alertes de Console Administrateur &#40;Analytique Platform System&#41;](understanding-admin-console-alerts.md).|  
|Composants de l’appliance et leur état|Cliquez sur **Appliance état** dans le menu supérieur, ou **accueil**.|  
|Analysez les requêtes (y compris les requêtes, les charges, les sauvegardes et restaurations)|Cliquez sur **Sessions** pour afficher les sessions actuellement actives ou récents.<br /><br />Cliquez sur **requêtes** pour afficher les requêtes actuellement actifs ou plus récentes. Les informations affichées pour les requêtes incluent des chargements, sauvegardes et restaurations.<br /><br />Cliquez sur **verrous** pour afficher les verrous actifs.|  
|Surveiller des informations supplémentaires pour les chargements, sauvegardes et restaurations.|Cliquez sur **charges** ou **sauvegardes/restaurations**.|  
|Informations sur les performances|Cliquez sur **Analyseur de performances**.|  
  
## <a name="see-also"></a>Voir aussi  
[Surveillance de l’appliance &#40;Analytique Platform System&#41;](appliance-monitoring.md)  
  
