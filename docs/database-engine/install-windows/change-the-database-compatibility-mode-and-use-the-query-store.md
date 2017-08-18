---
title: "Changer le mode de compatibilité de base de données et utiliser le magasin des requêtes | Microsoft Docs"
ms.custom: 
ms.date: 07/21/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- query plans [SQL Server], migrating
- upgrading SQL Server, migrating query plans
- plan guides [SQL Server], migrating query plans
ms.assetid: 7e02a137-6867-4f6a-a45a-2b02674f7e65
caps.latest.revision: 19
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 514fe566dd9a26d4a6244e8fb067f97678d2dbc7
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---

# <a name="change-the-database-compatibility-mode-and-use-the-query-store"></a>Modifier le mode de compatibilité de base de données et utiliser le magasin des requêtes
Dans SQL Server 2016 et SQL Server 2017, certaines modifications sont activées uniquement une fois que le niveau DATABASE_COMPATIBILITY d’une base de données a été changé. Cette opération a été effectuée pour plusieurs raisons :  
  
- Étant donné que la mise à niveau est une opération unidirectionnelle (il est impossible de faire passer le format de fichier à une version antérieure), le fait de séparer l’activation de nouvelles fonctionnalités pour en faire une opération distincte dans la base de données, comporte un intérêt.  Il est possible de rétablir un paramètre à un niveau DATABASE_COMPATIBILITY antérieur.  Le nouveau modèle réduit le nombre d’éléments devant se produire lors de l’interruption d’une fenêtre.  
  
- Les modifications apportées au processeur de requêtes peuvent avoir des effets complexes.  Même si une « bonne » modification apportée au système peut être intéressante pour la plupart des clients, elle peut provoquer une régression inacceptable sur une requête importante pour d’autres.  Le fait de séparer cette logique du processus de mise à niveau permet à des fonctionnalités, telles que le magasin des requêtes, d’atténuer rapidement les régressions de choix de plan ou même de les éviter complètement dans les serveurs de production.  
  
> [!NOTE]  
>  Si le niveau de compatibilité d'une base de données utilisateur est à 100 ou supérieur avant la mise à niveau, il reste le même après la mise à niveau. Si le niveau de compatibilité était à 90 avant la mise à niveau, dans la base de données mise à niveau, le niveau de compatibilité est défini à 100, ce qui correspond au niveau de compatibilité le plus bas pris en charge dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Les niveaux de compatibilité des bases de données tempdb, model, msdb et Resource databases sont définis sur le niveau de compatibilité actuel après la mise à niveau. La base de données système master conserve le niveau de compatibilité qu’elle avait avant la mise à niveau. 
  
 Le processus de mise à niveau permettant d’activer la nouvelle fonctionnalité du processeur de requêtes concerne le modèle de maintenance post-lancement du produit.  Certains de ces correctifs sont publiés sous l’indicateur de trace 4199.  Les clients nécessitant des correctifs peuvent les choisir sans provoquer de régressions inattendues pour d’autres clients.  Le modèle de maintenance post-lancement des correctifs logiciels du processeur de requêtes est documenté [ici](https://support.microsoft.com/en-us/kb/974006). À compter de SQL Server 2016, le passage à un nouveau niveau de compatibilité rend l’indicateur de trace 4199 inutile, dans la mesure où ces correctifs ne sont plus activés par défaut dans le tout dernier niveau de compatibilité.  Par conséquent, dans le cadre du processus de mise à niveau, il est important de confirmer que 4199 n’est pas activé une fois le processus de mise à niveau terminé.  
  
 Le flux de travail recommandé pour la mise à niveau du processeur de requêtes vers la dernière version du code est  :  
  
1.  Mettre à niveau une base de données vers SQL Server 2016 sans modifier son niveau de compatibilité (maintien au niveau précédent)  
  
2.  Activez le magasin des requêtes sur la base de données. Pour plus d’informations sur l’activation et l’utilisation du magasin des requêtes, consultez [Monitoring Performance By Using the Query Store](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md).  
  
3.  Patientez suffisamment pour collecter des données représentatives de la charge de travail.  
  
4.  Définissez le niveau de compatibilité de la base de données sur le niveau de compatibilité actuel. 

   >[!NOTE]
   >Le dernier niveau de compatibilité dépend de la version de SQL Server.
   >- SQL Server 2016 : 130
   >- SQL Server 2017 : 140

5. À l’aide de SQL Server Management Studio, évaluez l’existence de régressions des performances sur des requêtes spécifiques suite à la modification du niveau de compatibilité.
  
6.  En cas de régression, forcez le plan précédent dans le magasin des requêtes.  
  
7.  Si des plans de requête ne peuvent pas être forcés ou si les performances restent insuffisantes, envisagez de revenir au niveau de compatibilité précédent et à faire appel au support technique Microsoft.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher ou modifier le niveau de compatibilité d'une base de données](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md)  
  
  

