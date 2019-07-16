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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029011"
---
# <a name="installing-ssma-components-on-sql-server-sybasetosql"></a>Installation des composants SSMA sur SQL Server (SybaseToSQL)
Outre l’installation de SSMA pour l’utilisation de migration des données côté serveur, vous devez également installer les composants sur l’ordinateur qui est en cours d’exécution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ces composants incluent le pack d’extension SSMA qui prend en charge la migration des données et les fournisseurs de Sybase pour activer la connectivité du serveur à serveur.  
  
## <a name="ssma-for-sybase-extension-pack"></a>SSMA pour Sybase Extension Pack  
Le pack d’extension SSMA ajoute les bases de données, **sysdb** et **ssmatesterdb_syb**, à l’instance spécifiée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le **sysdb** base de données contient les tables et les procédures stockées qui sont nécessaires pour migrer des données. Le **ssmatester_syb** base de données contient le schéma **ssma_sybase_utilities**, dans lequel les objets (Tables, déclencheurs, les vues) utilisés par le composant de testeur SSMA sont créés.  
  
En outre, lorsque vous migrez des données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SSMA crée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] travaux de l’Agent lorsque le moteur de migration de données côté serveur est utilisé pour migrer les données.  
  
### <a name="installing-the-extension-pack"></a>L’installation du Pack d’Extension  
Vous pouvez installer le pack d’extension à tout moment avant de migrer des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
> Pour installer le pack d’extension, vous devez être membre du rôle serveur sysadmin sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Pour installer le pack d’extension**  
  
1.  Copiez SSMA pour Sybase Extension Pack. *n*. Install.exe, où *n* est le numéro de build, à l’ordinateur qui est en cours d’exécution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Double-cliquez sur SSMA pour Sybase Extension Pack. *n*. Install.exe.  
  
3.  Dans la page d’accueil, cliquez sur **suivant**.  
  
4.  Dans la page Contrat de licence utilisateur final, lisez le contrat de licence. Si vous acceptez, cochez la **J’accepte les termes du contrat de licence** case à cocher, puis cliquez sur **suivant**.  
  
5.  Dans la page Choisir un Type d’installation, cliquez sur **standard**.  
  
6.  Dans la page Prêt pour l’installation, cliquez sur **installer**.  
  
7.  Dans la page de la première étape d’Installation terminé, cliquez sur **suivant**.  
  
    Une boîte de dialogue s’affiche, dans laquelle vous sélectionnez l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour l’installation de pack d’extension.  
  
8.  Sélectionnez l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] où vous devez migrer les bases de données ASE et puis cliquez sur **suivant**.  
  
    L’instance par défaut a le même nom que l’ordinateur. Instances nommées seront suivis par une barre oblique inverse et le nom d’instance.  
  
9. Dans la page Paramètres de connexion, sélectionnez la méthode d’authentification, puis cliquez **suivant**.  
  
    L’authentification Windows utilisera vos informations d’identification Windows pour tenter de se connecter à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous sélectionnez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, vous devez entrer un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nom de connexion et mot de passe.  
  
10. Dans la page Gérer le serveur, sélectionnez **installer d’utilitaires de base de données** *n*, où *n* est le numéro de version, puis cliquez sur **suivant**.  
  
    Le **sysdb** base de données est créée et les procédures stockées sont créés dans cette base de données.  
  
    Si **installer la base de données testeur** activée le testeur **ssmatesterdb_syb** base de données sera créée.  
  
11. Pour installer les utilitaires vers une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sélectionnez **retourner aux instances**, puis cliquez sur **suivant**. Ou, pour quitter l’Assistant, cliquez sur **quitter**.  
  
### <a name="sql-server-database-objects"></a>Objets de base de données SQL Server  
Après avoir installé le pack d’extension, vous allez un, consultez un **ssma_syb.bcp_migration_packages** table dans le **sysdb** base de données. Vous verrez également les procédures stockées suivantes :  
  
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
  
Chaque fois que vous migrez des données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SSMA crée un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] travail de l’Agent. Ces tâches sont nommées **le package de migration de données ssma_syb {GUID}** et sont visibles dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nœud de l’Agent de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dans le dossier Jobs.  
  
## <a name="sybase-providers"></a>Fournisseurs de Sybase  
Lorsque vous migrez des données à partir de l’ASE à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQL Azure, la migration des données directement entre l’ASE et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQL Azure. Il ne traverse pas SSMA, car cela risque de ralentir la migration des données.  
  
### <a name="installing-the-sybase-providers"></a>Installez les fournisseurs de Sybase  
Les instructions suivantes fournissent les étapes d’installation de base pour l’installation de fournisseurs de Sybase. Les instructions exactes varie selon la version du programme d’installation de Sybase.  
  
> [!IMPORTANT]  
> Avant d’exécuter le programme d’installation, vérifiez que vous ne violent pas votre contrat de licence.  
  
1.  Exécutez le programme d’installation de Sybase ASE.  
  
2.  Sélectionnez le programme d’installation personnalisé.  
  
3.  Sur la page de sélection de fonctionnalités, sélectionnez les fournisseurs de données ODBC, OLE DB et ADO.NET.  
  
4.  Vérifiez les fonctionnalités sélectionnées, puis cliquez sur **Terminer** pour installer le fournisseur de données.  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour Sybase Client &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[Migration des bases de données de Sybase ASE pour SQL Server - Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
