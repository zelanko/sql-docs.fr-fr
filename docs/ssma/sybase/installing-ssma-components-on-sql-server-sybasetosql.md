---
title: Installation des composants SSMA sur SQL Server (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 5ad9e12c-2cdb-4dd2-8703-05a23242d19d
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 1fbc3a8f74b21bd5a53bdd874b5c41ef522e29f6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68029011"
---
# <a name="installing-ssma-components-on-sql-server-sybasetosql"></a>Installation des composants SSMA sur SQL Server (SybaseToSQL)
Outre l’installation de SSMA, pour l’utilisation de la migration des données côté serveur, vous devez également installer les composants sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]l’ordinateur qui exécute. Ces composants incluent le pack d’extension SSMA, qui prend en charge la migration des données et les fournisseurs Sybase pour activer la connectivité de serveur à serveur.  
  
## <a name="ssma-for-sybase-extension-pack"></a>SSMA pour le pack d’extension Sybase  
Le pack d’extension SSMA ajoute les bases de données, **sysdb** et **ssmatesterdb_syb**, à l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]spécifiée de. La base de données **sysdb** contient les tables et les procédures stockées nécessaires à la migration des données. La base de données **ssmatester_syb** contient le **ssma_sybase_utilities**de schéma, dans lequel les objets (tables, déclencheurs, vues) utilisés par le composant testeur SSMA sont créés.  
  
En outre, lorsque vous migrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , SSMA crée des travaux de l’agent lorsque le moteur de migration de données côté serveur est utilisé pour la migration des données.  
  
### <a name="installing-the-extension-pack"></a>Installation du pack d’extension  
Vous pouvez installer le pack d’extension à tout moment avant de migrer des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
> Pour installer le pack d’extension, vous devez être membre du rôle de serveur sysadmin sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Pour installer le pack d’extension**  
  
1.  Copie SSMA pour le pack d’extension Sybase. *n*. Installez. exe, où *n* est le numéro de build, sur l’ordinateur qui exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Double-cliquez sur SSMA pour le pack d’extension Sybase. *n*. Installez. exe.  
  
3.  Sur la page d'accueil, cliquez sur **Suivant**.  
  
4.  Sur la page contrat de licence utilisateur final, lisez le contrat de licence. Si vous acceptez, activez la case à cocher **J’accepte les termes du contrat de licence** , puis cliquez sur **suivant**.  
  
5.  Dans la page choisir le type d’installation, cliquez sur par **défaut**.  
  
6.  Dans la page prêt pour l’installation, cliquez sur **installer**.  
  
7.  Dans la page fin de la première étape de l’installation, cliquez sur **suivant**.  
  
    Une nouvelle boîte de dialogue s’affiche, dans laquelle vous sélectionnez l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de pour l’installation du pack d’extension.  
  
8.  Sélectionnez l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans laquelle vous allez migrer les bases de données ASE, puis cliquez sur **suivant**.  
  
    L’instance par défaut porte le même nom que l’ordinateur. Les instances nommées sont suivies d’une barre oblique inverse et du nom de l’instance.  
  
9. Sur la page Paramètres de connexion, sélectionnez la méthode d’authentification, puis cliquez sur **suivant**.  
  
    L’authentification Windows utilise vos informations d’identification Windows pour essayer de se connecter à l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de. Si vous sélectionnez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, vous devez entrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un nom de connexion et un mot de passe.  
  
10. Dans la page gérer le serveur, sélectionnez **installer la base de données des utilitaires** *n*, où *n* est le numéro de version, puis cliquez sur **suivant**.  
  
    La base de données **sysdb** est créée et les procédures stockées sont créées dans cette base de données.  
  
    Si l’option **installer la base de données du testeur** est cochée, le testeur **ssmatesterdb_syb** base de données sera créée.  
  
11. Pour installer les utilitaires sur une autre instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de, sélectionnez **revenir à instances**, puis cliquez sur **suivant**. Ou, pour quitter l’Assistant, cliquez sur **quitter**.  
  
### <a name="sql-server-database-objects"></a>SQL Server les objets de base de données  
Une fois que vous avez installé le pack d’extension, vous voyez s’afficher une table **ssma_syb. bcp_migration_packages** dans la base de données **sysdb** . Vous verrez également les procédures stockées suivantes :  
  
-   **bcp_clean_migration_data**  
  
-   **bcp_ensure_message_table**  
  
-   **bcp_insert_new_message**  
  
-   **bcp_post_process**  
  
-   **bcp_read_new_migration_messages**  
  
-   **bcp_save_migration_package**  
  
-   **bcp_smart_truncate**  
  
-   **bcp_start_migration_process**  
  
-   **get_jobstep_info**  
  
-   **stop_agent_process**  
  
Chaque fois que vous migrez des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]données vers, SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée un travail de l’agent. Ces travaux sont nommés **ssma_syb package de migration de données {GUID}** et sont visibles dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le nœud agent [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] de dans le dossier travaux.  
  
## <a name="sybase-providers"></a>Fournisseurs Sybase  
Lorsque vous migrez des données depuis [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ASE vers/SQL Azure, les données sont migrées directement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]entre ASE et/SQL Azure. Il ne passe pas par SSMA, car cela ralentirait la migration des données.  
  
### <a name="installing-the-sybase-providers"></a>Installation des fournisseurs Sybase  
Les instructions suivantes fournissent les étapes d’installation de base pour l’installation des fournisseurs Sybase. Les instructions exactes varient en fonction de la version du programme d’installation de Sybase.  
  
> [!IMPORTANT]  
> Avant d’exécuter le programme d’installation, vérifiez que vous ne respectez pas vos contrats de licence.  
  
1.  Exécutez le programme d’installation de Sybase ASE.  
  
2.  Sélectionnez installation personnalisée.  
  
3.  Dans la page sélection de fonctionnalités, sélectionnez les fournisseurs de données ODBC, OLE DB et ADO.NET.  
  
4.  Vérifiez les fonctionnalités sélectionnées, puis cliquez sur **Terminer** pour installer le fournisseur de données.  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour Sybase client &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[Migration de bases de données Sybase ASE vers SQL Server-Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
