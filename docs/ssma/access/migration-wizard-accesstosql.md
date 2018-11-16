---
title: Assistant de migration (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Migration Wizard dialog box
- Migration Wizard, adding Access databases
- Migration Wizard, Connect to SQL Azure
- Migration Wizard, Connect to SQL Server
- Migration Wizard, Link Tables
- Migration Wizard, Migration status
- Migration Wizard, New Project
- Migration Wizard, Selecting objects to migrate
ms.assetid: 5bab5914-b2ae-4795-8cf5-83e42d64bef2
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 62ef99767be3f228702a06d89ba52f5c3a9821fb
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51664818"
---
# <a name="migration-wizard-accesstosql"></a>Assistant de migration (AccessToSQL)
L’Assistant Migration vous guide à travers la migration d’une ou plusieurs bases de données à partir de l’accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. À l’aide de l’Assistant, vous serez créer un projet, ajouter des bases de données au projet, sélectionnez les objets à migrer et vous connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. Vous serez également convertir, charger et migrer des données et des schémas d’accès. Si vous le souhaitez, vous pouvez lier les tables de l’accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les tables ou de SQL Azure.  
  
La plupart des pages de l’Assistant de Migration contiennent les mêmes options que les boîtes de dialogue SSMA existants. Par conséquent, les pages d’Assistant sont décrites ici, et ensuite les liens sont fournis afin que vous pouvez en savoir plus sur les options individuelles. Si une page contient des options uniques, ils sont décrits ici.  
  
## <a name="starting-the-migration-wizard"></a>Démarrage de l’Assistant de Migration  
Par défaut, l’Assistant Migration s’affiche lorsque vous démarrez SSMA. Vous pouvez également démarrer l’Assistant sur le **fichier** menu en sélectionnant **Assistant Migration**.  
  
## <a name="welcome-page"></a>Page d'accueil  
La page d’accueil présente l’Assistant de Migration et fournit l’option suivante pour démarrer l’Assistant.  
  
**Lancer cet Assistant au démarrage.**  
Par défaut, SSMA démarre l’Assistant de Migration lorsque vous démarrez SSMA. Pour empêcher le démarrage automatique de l’Assistant, désactivez cette case à cocher.  
  
## <a name="create-new-project-page"></a>Créer une Page de projet  
La page Créer un nouveau projet est où vous entrez le nom, l’emplacement et migration projet type de fichier projet (la version de SQL Server utilisé pour la migration de cible). Pour plus d’informations, consultez [nouveau projet (SSMA)](https://msdn.microsoft.com/ca294f6d-eeb5-42ca-9306-156281a3f0f3)  
  
## <a name="add-access-databases-page"></a>Ajouter la Page d’accès aux bases de données  
La page Ajouter des bases de données Access est où vous ajoutez une ou plusieurs bases de données Access au projet. Vous pouvez ajouter des bases de données individuelles en cliquant sur **ajouter les bases de données**, puis en sélectionnant les bases de données à partir de la **Open** fenêtre. Ou, vous pouvez trouver des bases de données à l’aide de la **trouver les bases de données** bouton. Pour plus d'informations, consultez les rubriques suivantes :  
  
-   [Ajout et suppression de fichiers de base de données Access](adding-and-removing-access-database-files-accesstosql.md)  
  
-   [Assistant de bases de données (sélectionner des emplacements) de la recherche](https://msdn.microsoft.com/00b2d32a-998b-47a7-b25c-589b5bd6777a)  
  
-   [Rechercher l’Assistant de bases de données (sélectionner des fichiers)](https://msdn.microsoft.com/2f574a34-4bab-40a4-89a8-ad4907ffc3fd)  
  
-   [Assistant Rechercher des bases de données (Vérifier la sélection)](https://msdn.microsoft.com/62e20e03-50cc-4ac8-8072-524d194d2ec3)  
  
## <a name="select-objects-to-migrate-page"></a>Sélectionnez les objets à migrer de Page  
Sur la sélection des objets à la page de la migration, vous sélectionnez les objets à convertir. Vous pouvez sélectionner tous les objets, groupes d’objets ou des objets individuels.  
  
**Pour sélectionner des objets**  
  
1.  Développez **la métabase accès**, puis développez **bases de données**.  
  
2.  Effectuez une ou plusieurs des opérations suivantes :  
  
    -   Pour convertir toutes les bases de données, sélectionnez la case à cocher à côté **bases de données**.  
  
    -   Pour convertir ou omettre les bases de données individuelles, sélectionnez ou désactivez la case à cocher en regard du nom de la base de données.  
  
    -   Pour convertir ou omettre des requêtes, développez la base de données, puis cochez ou décochez la **requêtes** case à cocher.  
  
    -   Pour convertir ou omettre des tables individuelles, développez la base de données, puis **Tables**, puis sélectionnez ou désactivez la case à cocher en regard du tableau.  
  
Si vous avez de nombreux objets, vous souhaiterez utiliser les **sélection avancée de l’objet** options dans le volet droit pour filtrer l’accès des objets de base de données. Par exemple, si vous sélectionnez **Tables** dans le volet gauche, vous pouvez ensuite filtrer la liste des tables en entrant des chaînes dans le **filtre** boîte. Vous pouvez ensuite sélectionner ou effacer les tables filtrées pour la migration en utilisant les boutons en haut du volet.  
  
Pour plus d’informations sur le filtrage, consultez la section Options de [objet sélection avancée (SSMA courant)](https://msdn.microsoft.com/f53b0c79-5473-410a-a0dc-d8f544f7a63c).  
  
## <a name="connect-to-sql-server-page"></a>Se connecter à la Page SQL Server  
Sur la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] page, vous spécifiez les propriétés de connexion, puis connectez-vous à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [se connecter à SQL Server](https://msdn.microsoft.com/00e0432e-ec26-4ab4-af64-c9ca760e3541)  
  
> [!IMPORTANT]  
> Dès que la connexion réussit, vous rencontrerez **lier les Tables** page où vous avez la possibilité de lier les tables. Cliquez sur **suivant** et démarre la migration.  
  
## <a name="connect-to-sql-azure-page"></a>Se connecter à SQL Azure Page  
Sur la page connexion à SQL Azure, vous spécifiez les propriétés de connexion et puis se connectez à SQL Azure. Pour créer une nouvelle base de données azure, vous pouvez le faire à l’aide de **créer la base de données Azure** option qui s’affiche dans le, cliquez sur de **Parcourir** bouton. Pour plus d’informations, consultez [se connecter à SQL Azure](connect-to-azure-sql-db-accesstosql.md)  
  
> [!IMPORTANT]  
> Dès que la connexion réussit, vous rencontrerez **lier les Tables** page où vous avez la possibilité de lier les tables. Cliquez sur **suivant** bouton sur la page de liens pour démarrer la migration.  
  
## <a name="link-tables-page"></a>Page de Tables de lien  
La page de lier les Tables vous permet de lier vos tables Access d’origine à migrées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou des tables de SQL Azure. Liaison de tables modifie votre base de données Access afin que vos pages d’accès aux requêtes, formulaires, rapports et données utilisent les données dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure au lieu des données dans votre base de données Access.  
  
**Lier les tables**  
Sélectionnez le **liez des tables** case à cocher à lier à accéder aux tables migrées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou des tables de SQL Azure. Démarrer la migration, vous devez cliquer sur **suivant** bouton.  
  
## <a name="migration-status-page"></a>Page d’état de migration  
La page d’état de Migration affiche la progression de la conversion les schémas d’accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou les schémas de SQL Azure, le chargement des schémas convertis dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, et la migration des données.  
  
Pour plus d’informations sur cette page, consultez [convertir, charger et migrer](https://msdn.microsoft.com/4ec83e96-88a5-4b7b-8d5a-f3429d9a936b)  
  
## <a name="see-also"></a>Voir aussi  
[Mise en route avec SQL Server Migration Assistant pour Access &#40;AccessToSQL&#41;](../../ssma/access/getting-started-with-sql-server-migration-assistant-for-access-accesstosql.md)  
[Migration bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Reference(Access) d’Interface utilisateur](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
