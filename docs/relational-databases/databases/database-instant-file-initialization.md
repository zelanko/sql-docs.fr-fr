---
title: "Initialisation instantanée des fichiers de base de données | Microsoft Docs"
ms.custom: 
ms.date: 11/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- initializing files [SQL Server]
- instant file initialization [SQL Server]
- fast file initialization (SQL Server)
- file initialization [SQL Server]
- IFI [SQL Server]
ms.assetid: 1ad468f5-4f75-480b-aac6-0b01b048bd67
caps.latest.revision: "33"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 3f0ef2d2c733a0ab1f349d42d621303cc6c133a5
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="database-file-initialization"></a>Initialisation des fichiers de base de données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Les fichiers de données et les fichiers journaux sont initialisés pour remplacer toutes les données existantes laissées sur le disque par des fichiers précédemment supprimés. Les fichiers de données et les fichiers journaux sont d’abord initialisés en étant remplis avec des zéros quand vous effectuez une des opérations suivantes :  
  
- Créer une base de données.  
  
- Ajouter des fichiers journaux ou de données à une base de données existante.  
  
- Augmenter la taille d'un fichier existant (opérations de croissance automatique incluses).  
  
- Restaurer une base de données ou un groupe de fichiers.  
  
L'initialisation des fichiers augmente le temps d'exécution de ces opérations. En revanche, quand les données sont écrites dans les fichiers pour la première fois, le système d'exploitation n'a pas besoin de remplir ces fichiers à l'aide de zéros.  
  
# <a name="instant-file-initialization-ifi"></a>Initialisation instantanée de fichiers  
Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les fichiers de données peuvent être initialisés instantanément pour éviter les opérations de remplissage avec des zéros. L’initialisation instantanée des fichiers permet une exécution rapide des opérations mentionnées plus haut. L'initialisation instantanée des fichiers récupère l'espace disque utilisé sans le remplir avec des zéros. À la place, le contenu du disque est remplacé à mesure que de nouvelles données sont écrites dans les fichiers. Les fichiers journaux ne peuvent pas être initialisés instantanément.  
  
> [!NOTE]  
>  L’initialisation instantanée des fichiers n’est disponible que sur [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxppro](../../includes/winxppro-md.md)] ou [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] (ou versions ultérieures).  

> [!IMPORTANT]
> L’initialisation instantanée de fichiers est disponible seulement pour les fichiers de données. Les fichiers journaux sont toujours remplis de zéros à la création ou lors d’une augmentation de leur taille.
  
L’initialisation instantanée de fichiers est disponible seulement que si l’autorisation *SE_MANAGE_VOLUME_NAME* a été octroyée au compte de démarrage de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les membres du groupe Administrateurs Windows disposent de ce droit et peuvent l’attribuer aux autres utilisateurs en les ajoutant à la stratégie de sécurité **Effectuer les tâches de maintenance de volume** .  
  
L’utilisation de certaines fonctionnalités, comme [Transparent Data Encryption (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md), peuvent empêcher l’initialisation instantanée de fichiers.  
  
Pour accorder l'autorisation `Perform volume maintenance tasks` à un compte  
  
1.  Sur l’ordinateur où le fichier de sauvegarde doit être créé, ouvrez l’application **Stratégie de sécurité locale** (`secpol.msc`).  
  
2.  Dans le volet gauche, développez **Stratégies locales**, puis cliquez sur **Attribution des droits utilisateur**.  
  
3.  Dans le volet droit, double-cliquez sur **Effectuer des tâches de maintenance sur les volumes**.  
  
4.  Cliquez sur **Ajouter un utilisateur ou un groupe** et ajoutez tout compte d’utilisateur utilisé pour les sauvegardes.  
  
5.  Cliquez sur **Appliquer**, puis fermez toutes les boîtes de dialogue **Stratégie de sécurité locale** .  
  
### <a name="security-considerations"></a>Considérations relatives à la sécurité  
 Comme le contenu du disque supprimé n’est remplacé qu’au moment où de nouvelles données sont écrites dans les fichiers, il est éventuellement accessible à un principal non autorisé jusqu’à ce que d’autres données soient écrites sur cette zone spécifique du fichier de données. Même si le fichier de base de données est attaché à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le risque de divulgation de ces informations est limité par la liste de contrôle d’accès discrétionnaire (DACL, Discretionary Access Control List) du fichier. Cette liste DACL n'autorise l'accès au fichier qu'à l'administrateur local et au compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cependant, quand le fichier est détaché, un utilisateur ou un service ne bénéficiant pas de l’autorisation *SE_MANAGE_VOLUME_NAME* peut y accéder. Cette situation se présente aussi quand la base de données est sauvegardée : si le fichier de sauvegarde n’est pas protégé par une liste DACL appropriée, le contenu supprimé peut devenir accessible à un utilisateur ou à un service non autorisé.  
 
 Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé dans un environnement sécurisé, les gains de performance de l’activation de l’initialisation instantanée de fichiers peuvent primer sur les risques de sécurité et par conséquent justifier cette recommandation.
  
 Si le risque de divulgation du contenu supprimé constitue un problème, effectuez l’une et/ou l’autre des actions suivantes :  
  
- Assurez-vous toujours que les fichiers de sauvegarde et les fichiers de données détachés possèdent des listes DACL restrictives.  
  
- Désactivez l’initialisation instantanée des fichiers pour l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en révoquant l’autorisation *SE_MANAGE_VOLUME_NAME* au compte de démarrage du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
> La désactivation de l'initialisation instantanée des fichiers n'affecte que les fichiers créés ou dont la taille a augmenté après la révocation du droit de l'utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
  
