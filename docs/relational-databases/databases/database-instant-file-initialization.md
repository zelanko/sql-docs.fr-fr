---
title: Initialisation instantanée des fichiers de base de données
description: En savoir plus sur l’initialisation instantanée de fichiers et sur la manière de l’activer sur votre base de données SQL Server.
ms.custom: contperfq4
ms.date: 05/30/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- initializing files [SQL Server]
- instant file initialization [SQL Server]
- fast file initialization [SQL Server]
- file initialization [SQL Server]
- IFI [SQL Server]
- database instant file initialization [SQL Server]
ms.assetid: 1ad468f5-4f75-480b-aac6-0b01b048bd67
author: stevestein
ms.author: sstein
ms.openlocfilehash: a10e6f9cff886b18b8bc344270516aaf2b5577db
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85756257"
---
# <a name="database-instant-file-initialization"></a>Initialisation instantanée des fichiers de base de données
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
Dans cet article, vous découvrirez l’initialisation instantanée de fichiers et comment l’activer pour accélérer la croissance de vos fichiers de base de données SQL Server.  

Par défaut, les fichiers de données et les fichiers journaux sont initialisés pour remplacer toutes les données existantes laissées sur le disque par des fichiers précédemment supprimés. Les fichiers de données et les fichiers journaux sont d’abord initialisés en étant remplis avec des zéros quand vous effectuez les opérations suivantes :  
  
- Créer une base de données.  
- Ajouter des fichiers journaux ou de données à une base de données existante.  
- Augmenter la taille d'un fichier existant (opérations de croissance automatique incluses).  
- Restaurer une base de données ou un groupe de fichiers.  

Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l’initialisation instantanée des fichiers (IFI) permet une exécution plus rapide des opérations de fichier mentionnées précédemment, car elle libère de l’espace disque utilisé sans remplir cet espace avec des zéros. À la place, le contenu du disque est remplacé à mesure que de nouvelles données sont écrites dans les fichiers. Les fichiers journaux ne peuvent pas être initialisés instantanément.

## <a name="enable-instant-file-initialization"></a>Activer l’initialisation instantanée de fichiers

L’initialisation instantanée de fichiers est disponible seulement que si l’autorisation *SE_MANAGE_VOLUME_NAME* a été octroyée au compte de démarrage de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les membres du groupe Administrateurs Windows disposent de ce droit et peuvent l’attribuer aux autres utilisateurs en les ajoutant à la stratégie de sécurité **Effectuer les tâches de maintenance de volume** .  
> [!IMPORTANT]
> L’utilisation de certaines fonctionnalités, comme [Transparent Data Encryption (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md), peuvent empêcher l’initialisation instantanée de fichiers.  

> [!NOTE]
> À compter de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], vous pouvez accorder cette autorisation au compte de service au moment de l’installation. <br><br>Si vous effectuez [l’installation depuis une invite de commandes](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md), ajoutez l’argument /SQLSVCINSTANTFILEINIT ou cochez la case *Accorder le privilège Effectuer une tâche de maintenance en volume au service Moteur de base de données SQL Server* dans [l’Assistant Installation](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).
  
Pour accorder l'autorisation `Perform volume maintenance tasks` à un compte  
  
1.  Sur l’ordinateur où le fichier de données doit être créé, ouvrez l’application **Stratégie de sécurité locale** (`secpol.msc`).  
  
1.  Dans le volet gauche, développez **Stratégies locales**, puis cliquez sur **Attribution des droits utilisateur**.  
  
1.  Dans le volet droit, double-cliquez sur **Effectuer des tâches de maintenance sur les volumes**.  
  
1.  Cliquez sur **Ajouter un utilisateur ou un groupe** et ajoutez le compte qui exécute le service SQL Server.  
  
1.  Cliquez sur **Appliquer**, puis fermez toutes les boîtes de dialogue **Stratégie de sécurité locale** .  

1. Redémarrez le service SQL Server.

1. Consultez le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au démarrage.
   
  
    **S’applique à :** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (à compter de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP4, [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 et de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et versions ultérieures).
    1. Si le compte de démarrage de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dispose de l’autorisation *SE_MANAGE_VOLUME_NAME*, un message d’information similaire au suivant est journalisé :

        `Database Instant File Initialization: enabled. For security and performance considerations see the topic 'Database Instant File Initialization' in SQL Server Books Online. This is an informational message only. No user action is required.`

    1. Si le compte de démarrage de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’a **pas** l’autorisation *SE_MANAGE_VOLUME_NAME*, un message d’information similaire au suivant est journalisé :

        `Database Instant File Initialization: disabled. For security and performance considerations see the topic 'Database Instant File Initialization' in SQL Server Books Online. This is an informational message only. No user action is required.`
    > [!NOTE]
    > Vous pouvez utiliser la colonne *instant_file_initialization_enabled* dans la vue de gestion dynamique [sys.dm_server_services](../../relational-databases/system-dynamic-management-views/sys-dm-server-services-transact-sql.md) pour déterminer si l’initialisation instantanée de fichiers est activée.

## <a name="security-considerations"></a>Considérations relatives à la sécurité

Nous vous recommandons d’activer l’initialisation instantanée de fichiers, car les avantages peuvent l’emporter sur le risque de sécurité.

Lors de l’utilisation de l’initialisation instantanée de fichiers, le contenu du disque supprimé n’est remplacé que lorsque de nouvelles données sont écrites dans les fichiers. Pour cette raison, le contenu supprimé est éventuellement accessible à un principal non autorisé jusqu’à ce que d’autres données soient écrites sur cette zone spécifique du fichier de données.

Même si le fichier de base de données est attaché à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le risque de divulgation de ces informations est limité par la liste de contrôle d’accès discrétionnaire (DACL, Discretionary Access Control List) du fichier. Cette liste DACL n'autorise l'accès au fichier qu'à l'administrateur local et au compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cependant, quand le fichier est détaché, un utilisateur ou un service ne bénéficiant pas de l’autorisation *SE_MANAGE_VOLUME_NAME* peut y accéder.

Des considérations similaires sont disponibles dans les cas suivants :

* *La base de données est sauvegardée.* Si le fichier de sauvegarde n’est pas protégé par une liste DACL appropriée, le contenu supprimé peut devenir inaccessible à un utilisateur ou service non autorisé.  

* *Un fichier est développé à l’aide de l’IFI (initialisation instantanée de fichiers)* . Un administrateur SQL Server peut potentiellement accéder au contenu de la page brute et voir le contenu précédemment supprimé.

* *Les fichiers de base de données sont hébergés sur un réseau de zone de stockage*. Il est également possible que le réseau de zone de stockage présente toujours les nouvelles pages préinitialisées. Or, laisser le système d’exploitation réinitialiser les pages peut représenter une charge supplémentaire non nécessaire.

Si le risque de divulgation du contenu supprimé constitue un problème, effectuez l’une et/ou l’autre des actions suivantes :  
  
- Assurez-vous toujours que les fichiers de sauvegarde et les fichiers de données détachés possèdent des listes DACL restrictives.  
- Désactivez l’initialisation de fichiers instantanée pour l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].    Pour ce faire, révoquez *SE_MANAGE_VOLUME_NAME* du compte de démarrage du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
    
    > [!NOTE]
    > La désactivation augmentera les durées d’allocation des fichiers de données et n'affecte que les fichiers créés ou dont la taille a augmenté après la révocation du droit de l'utilisateur.
  
## <a name="see-also"></a>Voir aussi  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)
