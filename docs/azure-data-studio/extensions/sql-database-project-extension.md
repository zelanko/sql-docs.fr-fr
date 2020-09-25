---
title: Extension des projets SQL Database
description: Installez et utilisez l’extension des projets SQL Database pour Azure Data Studio.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: dzsquared
ms.author: drskwier
ms.reviewer: maghan
ms.custom: ''
ms.date: 09/22/2020
ms.openlocfilehash: 65006891a6633a75482f9a32c328dea0d8bf76fc
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91123103"
---
# <a name="sql-database-projects-extension-preview"></a>Extension des projets SQL Database (préversion)

L’extension des projets SQL Database (préversion) est une extension pour le développement de bases de données SQL dans un environnement de développement basé sur un projet. 

## <a name="features"></a>Fonctionnalités

1. Créer un projet à partir d’une base de données connectée.
2. Créer un nouveau projet vide.
3. Ouvrez un projet créé précédemment dans [Azure Data Studio](sql-database-project-extension-getting-started.md) ou dans [SQL Server Data Tools](../../ssdt/sql-server-data-tools.md).
4. Modifiez un projet en ajoutant ou en supprimant une table, une vue, une procédure stockée ou des scripts personnalisés dans le projet.
5. Organisez les fichiers/scripts dans des dossiers.
6. Ajoutez des références aux bases de données système ou au package dac (DACPAC) d’un utilisateur.
7. Créez un projet unique.
8. Déployez un projet unique.
9. Chargez les détails de connexion (authentification Windows SQL) et les variables SQLCMD à partir du profil de déploiement.

## <a name="install-the-sql-database-projects-extension"></a>Installer l’extension des projets SQL Database

1. Ouvrez le gestionnaire d’extensions pour accéder aux extensions disponibles.  Pour cela, sélectionnez l’icône des extensions ou l’option **Extensions** dans le menu **Affichage**.
2. Identifiez l’extension *des projets SQL Database* en tapant tout ou partie du nom dans la zone de recherche de l’extension. Sélectionnez une extension disponible pour afficher ses détails.

   ![Installer l’extension](media/sql-database-projects-extension/install-database-projects.png)

3. Sélectionnez l’extension de votre choix et **installez-la**.
4. Sélectionnez **Recharger** pour activer l’extension (nécessaire uniquement la première fois que vous installez une extension).
5. Sélectionnez l’icône fichiers à partir de la barre d’activité ou sélectionnez **Explorer** dans le menu **Affichage**. Une nouvelle icône pour les**Projets**  est désormais disponible.

   > [!NOTE]
   > Le kit SDK .NET Core est requis pour la fonctionnalité de génération de projet, et vous serez invité à l’installer s’il ne peut pas être détecté par l’extension.  Le kit SDK .NET Core (3.1 ou version ultérieure) peut être téléchargé et installé à partir de [https://dotnet.microsoft.com/download/dotnet-core/3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1).

   > [!NOTE]
   > Il est recommandé d’installer l’extension de [Comparaison de schémas](schema-compare-extension.md) avec l’extension des projets SQL Database pour bénéficier de toutes les fonctionnalités.

## <a name="known-limitations"></a>Limitations connues

1. L’ajout de références de projet et le chargement de références de projet existantes dans la section Azure Data Studio ne sont pas pris en charge actuellement.
2. Le chargement de fichiers en tant que lien n’est pas pris en charge dans la section Azure Data Studio. Toutefois, les fichiers sont chargés au niveau supérieur dans l’arborescence et la build incorpore ces fichiers comme prévu.
3. L’ajout et le chargement du script de déploiement avant publication dans la section n’est pas pris en charge. Toutefois, si vous ajoutez manuellement ces fichiers au projet, ils sont honorés au moment de la génération.
4. Les objets SQLCLR dans le projet ne sont pas pris en charge dans la version .NET Core de DacFx.
5. Les tâches (génération/publication) ne sont pas définies par l’utilisateur.
6. Publier les cibles définies par DacFx.
7. L’intégration du contrôle de code source et la création d’un nouveau projet ne créent pas automatiquement le fichier .gitignore.
8. La prise en charge de l’environnement WSL est limitée.

## <a name="next-steps"></a>Étapes suivantes

- [Bien démarrer avec l’extension SQL Database Projects](sql-database-project-extension-getting-started.md)
- [Générer et publier un projet avec l’extension des projets SQL Database pour Azure Data Studio](sql-database-project-extension-build.md)