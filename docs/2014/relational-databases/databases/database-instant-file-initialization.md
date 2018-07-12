---
title: Initialisation instantanée des fichiers de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- initializing files [SQL Server]
- instant file initializations [SQL Server]
- fast file initialization (SQL Server)
- file initialization [SQL Server]
ms.assetid: 1ad468f5-4f75-480b-aac6-0b01b048bd67
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: da60e00ce0162a553d9ecf68368edd3dde193a08
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180099"
---
# <a name="database-instant-file-initialization"></a>Initialisation instantanée des fichiers de base de données
  Les fichiers de données et les fichiers journaux sont initialisés pour remplacer toutes les données existantes laissées sur le disque par des fichiers précédemment supprimés. Les fichiers de données et les fichiers journaux sont d'abord initialisés en étant remplis avec des zéros quand vous effectuez l'une des opérations suivantes :  
  
-   créer une base de données ;  
  
-   ajouter des fichiers, un journal ou des données à une base de données existante ;  
  
-   augmenter la taille d'un fichier existant (opérations de croissance automatique incluses) ;  
  
-   Restaurer une base de données ou un groupe de fichiers.  
  
 L'initialisation des fichiers augmente le temps d'exécution de ces opérations. En revanche, quand les données sont écrites dans les fichiers pour la première fois, le système d'exploitation n'a pas besoin de remplir ces fichiers à l'aide de zéros.  
  
## <a name="instant-file-initialization"></a>Initialisation instantanée de fichiers  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les fichiers de données peuvent être initialisés instantanément. Cela permet une exécution rapide des opérations mentionnées plus haut. L'initialisation instantanée des fichiers récupère l'espace disque utilisé sans le remplir avec des zéros. À la place, le contenu du disque est remplacé à mesure que de nouvelles données sont écrites dans les fichiers. Les fichiers journaux ne peuvent pas être initialisés instantanément.  
  
> [!NOTE]  
>  L’initialisation instantanée des fichiers n’est disponible que sur [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxppro](../../includes/winxppro-md.md)] ou [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] (ou versions ultérieures).  
  
 L'initialisation instantanée des fichiers n'est disponible que si l'autorisation SE_MANAGE_VOLUME_NAME a été octroyée au compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER). Les membres du groupe Administrateurs Windows disposent de ce droit et peuvent l’attribuer aux autres utilisateurs en les ajoutant à la stratégie de sécurité **Effectuer les tâches de maintenance de volume** . Pour plus d'informations sur l'affectation de droits de l'utilisateur, consultez la documentation de Windows.  
  
 L'initialisation instantanée des fichiers n'est pas disponible quand le chiffrement transparent des données est activé.  
  
 Pour accorder l'autorisation `Perform volume maintenance tasks` à un compte  
  
1.  Sur l’ordinateur où le fichier de sauvegarde doit être créé, ouvrez le `Local Security Policy` application (`secpol.msc`).  
  
2.  Dans le volet gauche, développez **Stratégies locales**, puis cliquez sur **Attribution des droits utilisateur**.  
  
3.  Dans le volet droit, double-cliquez sur **Effectuer des tâches de maintenance sur les volumes**.  
  
4.  Cliquez sur **Ajouter un utilisateur ou un groupe** et ajoutez tout compte d’utilisateur utilisé pour les sauvegardes.  
  
5.  Cliquez sur **appliquer**, puis fermez toutes les `Local Security Policy` boîtes de dialogue.  
  
### <a name="security-considerations"></a>Considérations relatives à la sécurité  
 Comme le contenu du disque supprimé n'est remplacé qu'au moment où de nouvelles données sont écrites dans les fichiers, il est éventuellement accessible à un principal non autorisé. Même si le fichier de base de données est attaché à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le risque de divulgation de ces informations est limité par la liste de contrôle d'accès discrétionnaire (DACL, Discretionary Access Control List) du fichier. Cette liste DACL n'autorise l'accès au fichier qu'à l'administrateur local et au compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cependant, quand le fichier est détaché, un utilisateur ou un service ne bénéficiant pas de l'autorisation SE_MANAGE_VOLUME_NAME peut y accéder. Un risque similaire existe quand la base de données est sauvegardée. Un service ou un utilisateur non autorisé peut accéder au contenu supprimé si le fichier de sauvegarde n'est pas protégé par une liste DACL appropriée.  
  
 Si le risque de divulgation du contenu supprimé constitue un problème, effectuez l'une et/ou l'autre des actions suivantes :  
  
-   Assurez-vous toujours que les fichiers de sauvegarde et les fichiers de données détachés possèdent des listes DACL restrictives.  
  
-   Désactivez l'initialisation instantanée des fichiers pour l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en révoquant l'autorisation SE_MANAGE_VOLUME_NAME au compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  La désactivation de l'initialisation instantanée des fichiers n'affecte que les fichiers créés ou dont la taille a augmenté après la révocation du droit de l'utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
