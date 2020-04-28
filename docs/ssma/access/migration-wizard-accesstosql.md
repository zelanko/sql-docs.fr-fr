---
title: Assistant Migration (AccessToSQL) | Microsoft Docs
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
ms.openlocfilehash: 658487186924fe5547edee70425524b2b4e3be6c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68083592"
---
# <a name="migration-wizard-accesstosql"></a>Assistant Migration (AccessToSQL)
L’Assistant Migration vous guide tout au long de la migration d’une ou plusieurs bases de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données d’accès à ou SQL Azure. À l’aide de l’Assistant, vous allez créer un projet, ajouter des bases de données au projet, sélectionner les objets à migrer, puis vous connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. Vous allez également convertir, charger et migrer les schémas d’accès et les données. Si vous le souhaitez, vous pouvez lier des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables d’accès à des tables ou SQL Azure.  
  
La plupart des pages de l’Assistant Migration contiennent les mêmes options que les boîtes de dialogue SSMA existantes. Par conséquent, les pages de l’Assistant sont décrites ici, puis des liens sont fournis afin que vous puissiez en savoir plus sur les différentes options. Si une page contient des options uniques, elles sont documentées ici.  
  
## <a name="starting-the-migration-wizard"></a>Démarrage de l’Assistant Migration  
Par défaut, l’Assistant Migration s’affiche lorsque vous démarrez SSMA. Vous pouvez également démarrer l’Assistant dans le menu **fichier** en sélectionnant **Assistant Migration**.  
  
## <a name="welcome-page"></a>Page d’accueil  
La page d’accueil présente l’Assistant Migration et fournit l’option suivante pour démarrer l’Assistant.  
  
**Lancez cet Assistant au démarrage.**  
Par défaut, SSMA démarre l’Assistant Migration lorsque vous démarrez SSMA. Pour empêcher le démarrage automatique de l’Assistant, désactivez cette case à cocher.  
  
## <a name="create-new-project-page"></a>Page créer un nouveau projet  
La page créer un nouveau projet vous permet d’entrer le nom du fichier projet, l’emplacement et le type de projet de migration (la version de la SQL Server cible utilisée pour la migration). Pour plus d’informations, consultez [New Project (SSMA)](https://msdn.microsoft.com/ca294f6d-eeb5-42ca-9306-156281a3f0f3) .  
  
## <a name="add-access-databases-page"></a>Page Ajouter des bases de données Access  
La page Ajouter des bases de données Access est l’emplacement où vous ajoutez une ou plusieurs bases de données Access au projet. Vous pouvez ajouter des bases de données individuelles en cliquant sur **Ajouter des bases**de données, puis en sélectionnant les bases de données dans la fenêtre **ouvrir** . Vous pouvez rechercher des bases de données à l’aide du bouton **Rechercher des bases de données** . Pour plus d'informations, voir les rubriques suivantes :  
  
-   [Ajout et suppression de fichiers de base de données Access](adding-and-removing-access-database-files-accesstosql.md)  
  
-   [Assistant Rechercher des bases de données (Sélectionner des emplacements)](https://msdn.microsoft.com/00b2d32a-998b-47a7-b25c-589b5bd6777a)  
  
-   [Assistant Rechercher des bases de données (Sélectionner des fichiers)](https://msdn.microsoft.com/2f574a34-4bab-40a4-89a8-ad4907ffc3fd)  
  
-   [Assistant Rechercher des bases de données (Vérifier la sélection)](https://msdn.microsoft.com/62e20e03-50cc-4ac8-8072-524d194d2ec3)  
  
## <a name="select-objects-to-migrate-page"></a>Page Sélectionner les objets à migrer  
Dans la page Sélectionner les objets à migrer, vous sélectionnez les objets à convertir. Vous pouvez sélectionner tous les objets, groupes d’objets ou objets individuels.  
  
**Pour sélectionner des objets**  
  
1.  Développez **accès-métabase**, puis développez **bases de données**.  
  
2.  Effectuez une ou plusieurs des actions suivantes :  
  
    -   Pour convertir toutes les bases de données, activez la case à cocher en regard de **bases de données**.  
  
    -   Pour convertir ou omettre des bases de données, activez ou désactivez la case à cocher en regard du nom de la base de données.  
  
    -   Pour convertir ou omettre des requêtes, développez la base de données, puis activez ou désactivez la case à cocher **requêtes** .  
  
    -   Pour convertir ou omettre des tables individuelles, développez la base de données, développez **tables**, puis activez ou désactivez la case à cocher en regard de la table.  
  
Si vous avez de nombreux objets, vous souhaiterez peut-être utiliser les options **avancées de sélection d’objet** dans le volet droit pour filtrer les objets de base de données Access. Par exemple, si vous sélectionnez **tables** dans le volet gauche, vous pouvez filtrer la liste des tables en entrant des chaînes dans la zone de **filtre** . Vous pouvez ensuite sélectionner ou effacer les tables filtrées pour la migration à l’aide des boutons situés en haut du volet.  
  
Pour plus d’informations sur le filtrage, consultez la section Options de la [Sélection avancée d’objets (SSMA Common)](https://msdn.microsoft.com/f53b0c79-5473-410a-a0dc-d8f544f7a63c).  
  
## <a name="connect-to-sql-server-page"></a>Page se connecter à SQL Server  
Sur la page se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connecter à, vous spécifiez les propriétés de connexion, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]puis vous vous connectez à. Pour plus d’informations, consultez [se connecter à SQL Server](connect-to-sql-server-accesstosql.md).
  
> [!IMPORTANT]  
> Dès que la connexion est établie, la page lier les **tables** s’affiche, dans laquelle vous pouvez lier les tables. Cliquez sur **suivant** pour démarrer la migration.  
  
## <a name="connect-to-sql-azure-page"></a>Page se connecter à SQL Azure  
Sur la page se connecter à SQL Azure, vous spécifiez les propriétés de connexion, puis vous vous connectez à SQL Azure. Pour créer une nouvelle base de données Azure, vous pouvez utiliser l’option **créer une base de données Azure** qui apparaît sur le bouton **Parcourir** . Pour plus d’informations, consultez [se connecter à SQL Azure](connect-to-azure-sql-db-accesstosql.md)  
  
> [!IMPORTANT]  
> Dès que la connexion est établie, la page lier les **tables** s’affiche, dans laquelle vous pouvez lier les tables. Cliquez sur le bouton **suivant** dans la page Liens pour démarrer la migration.  
  
## <a name="link-tables-page"></a>Page lier les tables  
La page lier les tables vous permet de lier vos tables Access d’origine aux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables migrées ou SQL Azure. La liaison de tables modifie votre base de données Access afin que vos requêtes, formulaires, rapports et pages d’accès aux données utilisent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les données de la base de données ou SQL Azure au lieu des données de votre base de données Access.  
  
**Lier les tables**  
Activez la case à cocher **lier les tables** pour lier les tables d' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accès aux tables migrées ou SQL Azure. Pour démarrer la migration, vous devez cliquer sur le bouton **suivant** .  
  
## <a name="migration-status-page"></a>Page État de la migration  
La page État de la migration affiche la progression de la conversion des schémas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’accès vers ou SQL Azure schémas, le chargement des schémas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convertis dans ou SQL Azure, puis la migration des données.  
  
Pour plus d’informations sur cette page, consultez [convertir, charger et migrer](https://msdn.microsoft.com/4ec83e96-88a5-4b7b-8d5a-f3429d9a936b)  
  
## <a name="see-also"></a>Voir aussi  
[Prise en main avec Assistant Migration SQL Server pour Access &#40;AccessToSQL&#41;](../../ssma/access/getting-started-with-sql-server-migration-assistant-for-access-accesstosql.md)  
[Migration de bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Référence de l’interface utilisateur (accès)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
