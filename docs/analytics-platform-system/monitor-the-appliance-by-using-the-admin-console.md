---
title: Surveiller avec la console d’administration
description: Pour Analytics Platform System, la console d’administration est une application Web qui couvre les informations relatives à l’État, à l’intégrité et aux performances de l’appliance. Les utilisateurs se connectent à la console d’administration via un navigateur Internet.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 977e38016fbb58356d22ccfc5f783539e5f852d5
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74400942"
---
# <a name="monitor-the-appliance-with-the-admin-console---analytics-platform-system"></a>Surveiller l’appliance à l’aide de la console d’administration-analyse système de plateforme
La console d’administration est une application Web SQL Server PDW qui couvre les informations relatives à l’État, à l’intégrité et aux performances de l’appliance. Les utilisateurs se connectent à la console d’administration via Internet Explorer.  
  
## <a name="About"></a>À propos de la console d’administration  
![Accueil de la console des appliances](./media/monitor-the-appliance-by-using-the-admin-console/SQL_Server_PDW_AdminConsol_ApplHome.png "SQL_Server_PDW_AdminConsol_ApplHome")  
  
**Appliance**  
Accueil  
Fournit un résumé rapide de l’état de l’appliance.  
  
Intégrité  
Affiche la topologie de l’appliance avec des indicateurs indiquant l’intégrité de chaque composant analysé au sein de chaque nœud. Vous permet d’afficher l’état actuel des nœuds et des propriétés individuels des composants de nœud.  
  
Affiche les alertes matérielles et logicielles.  
  
Analyseur de performances  
Affiche les graphiques de l’analyseur de performances.  
  
**Parallel Data Warehouse**  
Accueil  
Fournit un récapitulatif rapide de l’état du PDW.  
  
Sessions  
Affiche les sessions utilisateur PDW actives. Cela peut vous aider à surveiller la contention des ressources.  
  
Requêtes  
Affiche la liste des requêtes en cours d’exécution et des requêtes terminées récemment. Il affiche les erreurs associées, le cas échéant. Permet également d’afficher les détails du plan d’exécution de la requête et les informations d’exécution du nœud.  
  
Charges  
Affiche les plans de charge, l’état actuel des chargements PDW et les erreurs associées, le cas échéant.  
  
Sauvegardes/restaurations  
Affiche un journal des opérations de sauvegarde et de restauration PDW.  
  
Intégrité  
Affiche la topologie PDW avec des indicateurs indiquant l’intégrité de chaque composant analysé au sein de chaque nœud. Vous permet d’afficher l’état actuel des nœuds et des propriétés individuels des composants de nœud.  
  
Affiche les alertes matérielles et logicielles.  
  
Ressources  
Affiche la liste des verrous de ressources PDW et leur état actuel.  
  
Stockage  
Résume l’utilisation du stockage PDW.  
  
Analyseur de performances  
Affiche les graphiques de l’analyseur de performances PDW.  
 
> [!NOTE]  
> La console d’administration a une résolution d’écran 1024x768. La console d’administration s’affiche mieux avec une résolution d’écran de 1280 X 1024 ou supérieure.  
  
## <a name="Connect"></a>Connexion à la console d’administration  
Pour vous connecter à la console d’administration, requiert :  
  
-   Au moins Internet Explorer version 10.  
  
-   Autorisations d’accès à la console d’administration. <!-- MISSING LINKS See [Grant Permissions to Use the Admin Console &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-use-the-admin-console-sql-server-pdw.md).  -->  
  
-   Adresse IP du cluster de nœuds de contrôle.  Procurez-vous auprès de votre administrateur SQL Server PDW.  
  
Pour vous connecter à la console d’administration, utilisez Internet Explorer et HTTPS pour accéder à l’adresse IP du cluster de nœuds de contrôle. Par exemple, si l’adresse IP du cluster de nœuds de `10.192.63.102`contrôle est `https://10.192.63.102` , entrez dans la barre d’adresse de votre navigateur. Le premier écran vous demande votre **connexion** et votre **mot de passe**. Fournissez une connexion d’authentification SQL Server et un mot de passe, ou bien une connexion d’authentification Windows et un mot de passe Windows. Si vous utilisez une connexion d’authentification Windows, la console d’administration utilise l’emprunt d’identité.  
  
## <a name="RelatedTasks"></a>Tâches de la console d’administration  
La console d’administration vous permet d’analyser les éléments suivants :  
  
|||  
|-|-|  
|**Type d’informations**|**Comment accéder à dans la console d’administration**|  
|État global de l’appliance|Cliquez sur état de l' **Appliance** dans le menu supérieur ou **page d’hébergement**.|  
|Alertes|Cliquez sur **Alertes**. Pour plus d’informations, voir fonctionnement des alertes de la [console d’administration &#40;Analytics Platform System&#41;](understanding-admin-console-alerts.md).|  
|Composants de l’appliance et leur état|Cliquez sur état de l' **Appliance** dans le menu supérieur ou **page d’hébergement**.|  
|Surveiller les demandes (y compris les requêtes, les chargements, les sauvegardes et les restaurations)|Cliquez sur **sessions** pour voir les sessions actives ou récentes.<br /><br />Cliquez sur **requêtes** pour afficher les requêtes actives ou récentes. Les informations affichées pour les requêtes incluent les charges, les sauvegardes et les restaurations.<br /><br />Cliquez sur **verrous** pour afficher les verrous actifs.|  
|Surveiller des informations supplémentaires pour les chargements, les sauvegardes et les restaurations.|Cliquez sur **chargements** ou **sauvegardes/restaurations**.|  
|Informations sur les performances|Cliquez sur **Analyseur de performances**.|  
  
## <a name="see-also"></a>Voir aussi  
[Système de plateforme d’analyse de &#40;Analytics de l’appliance&#41;](appliance-monitoring.md)  
  
