---
title: Bien démarrer avec l’extension SQL Database Projects
description: Installer et utiliser l’extension des projets SQL Database (préversion) pour Azure Data Studio
ms.custom: seodec18
ms.date: 07/30/2020
ms.reviewer: drskwier, maghan, sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: dzsquared
ms.author: drskwier
ms.openlocfilehash: 9f7f277d3e038b42f72a887c8fa7e08739be9192
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88180697"
---
# <a name="getting-started-with-the-sql-database-projects-extension-preview"></a>Bien démarrer avec l’extension SQL Database Projects (préversion)

Cet article décrit trois façons de commencer à utiliser l’extension des projets SQL Database :
1. Créez un projet de base de données en accédant à l’icône **Projets** sous Explorer ou en recherchant **Nouveau projet de base de données** dans la palette de commandes.
2. Les projets de base de données existants peuvent être ouverts via **Ouvrir un projet de base de données** dans la palette de commandes.
3. Démarrez à partir d’une base de données existante à l’aide de **Importer un nouveau projet de base de données** à partir de la palette de commandes.

   ![Nouvelle icône](media/extensions/sql-database-projects-extension/projects-viewlet.png)


### <a name="create-an-empty-database-project"></a>Créer un projet de base de données vide

 Dans l’icône **Projets** sous **Explorer**, cliquez sur le bouton **Nouveau projet** et entrez un nom de projet dans l’entrée de texte qui s’affiche.  Dans la boîte de dialogue « Sélectionner un dossier » qui s’affiche, sélectionnez un répertoire pour le dossier du projet, le fichier. sqlproj et tout autre contenu dans lequel se trouve.
Le projet vide est ouvert et visible dans l’icône **Projets** pour modification.

### <a name="open-an-existing-project"></a>Ouvrir un projet existant

Dans l’icône **Projets**, cliquez sur le bouton **Ouvrir le projet** et ouvrez un fichier *.sqlproj* existant à partir du sélecteur de fichiers qui s’affiche. Les projets existants peuvent provenir d’Azure Data Studio ou [Visual Studio SQL Server Data Tools](../ssdt/sql-server-data-tools.md).

Le projet vide est ouvert et son contenu visible dans l’icône **Projets** pour modification.

### <a name="create-a-database-project-from-an-existing-database"></a>Créer un projet de base de données à partir d’une base de données existante

Dans l’icône**Projet**, cliquez sur le bouton **Importer le projet à partir de la base de données** et connectez-vous à un SQL Server.  Une fois la connexion établie, sélectionnez une base de données dans la liste des bases de données disponibles et définissez le nom du projet.

Enfin, sélectionnez une structure cible pour l’extraction.  Le nouveau projet est ouvert et contient des scripts SQL pour le contenu de la base de données sélectionnée.

## <a name="build-and-publish"></a>Générer et publier

Le déploiement du projet de base de données est effectué dans l’extension des projets SQL Database pour Azure Data Studio en générant le projet dans un [fichier d’application de la couche Données](../relational-databases/data-tier-applications/data-tier-applications.md) (DACPAC) et en le publiant sur une plateforme prise en charge. Pour plus d’informations sur ce processus, veuillez consulter [Générer et publier un projet](sql-database-project-extension-build.md).

## <a name="schema-compare"></a>Comparaison de schémas
L’extension de projets SQL Database interagit avec [l’extension de comparaison de schémas](schema-compare-extension.md), si elle est installée, pour comparer le contenu d’un projet à une base de données dacpac ou existante.  La comparaison de schémas résultante peut être utilisée pour visualiser et appliquer les différences entre la source et la cible.

## <a name="next-steps"></a>Étapes suivantes

- [Générer et publier un projet avec l’extension des projets SQL Database pour Azure Data Studio](sql-database-project-extension-build.md)