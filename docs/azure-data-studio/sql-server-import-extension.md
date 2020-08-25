---
title: Extension d’importation SQL Server
description: Découvrez comment installer et utiliser l’extension SQL Server Import (préversion) pour Azure Data Studio, un Assistant qui convertit des fichiers .txt et .csv en une table SQL.
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu, maghan, sstein
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 9ecee71588cb54cb23c813cf5009b92159cf94d6
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88765918"
---
# <a name="sql-server-import-extension-preview"></a>Extension d’importation SQL Server (préversion)

L’extension d’importation SQL Server (préversion) convertit les fichiers. txt et. csv en une table SQL. Cet assistant utilise un framework Microsoft Research appelé [Program Synthesis using Examples (PROSE)](https://microsoft.github.io/prose/) pour analyser intelligemment le fichier avec une entrée utilisateur minimale. Il s’agit d’une infrastructure puissante pour le data wrangling, et il s’agit de la même technologie que celle derrière le remplissage rapide dans Microsoft Excel

Pour en savoir plus sur la version SSMS de cette fonctionnalité, vous pouvez lire [cet article](../relational-databases/import-export/import-flat-file-wizard.md).


## <a name="install-the-sql-server-import-extension"></a>Installer l’extension d’importation SQL Server

1. Pour ouvrir le gestionnaire d’extensions et accéder aux extensions disponibles, sélectionnez l’icône d’extensions ou sélectionnez **Extensions** dans le menu **Affichage**.
2. Sélectionnez une extension disponible pour afficher ses détails.

   ![Gestionnaire de l’extension d’importation](media/sql-server-import-extension/import-wizard-install.png)

1. Sélectionnez l’extension de votre choix et **installez-la**.
2. Sélectionnez **Recharger** pour activer l’extension (nécessaire uniquement la première fois que vous installez une extension).

## <a name="start-import-wizard"></a>Démarrer l’assistant d’importation

1. Pour démarrer l’importation SQL Server, commencez par établir une connexion à un serveur sous l’onglet Serveurs.
2. Après avoir établi une connexion, explorez la base de données cible dans laquelle vous souhaitez importer un fichier dans une table SQL.
3. Cliquez avec le bouton droit sur la base de données, puis cliquez sur **Assistant d’importation**.
    ![ouvrir l’assistant d’importation](media/sql-server-import-extension/open-import-wizard.png)

## <a name="importing-a-file"></a>Importation d’un fichier
1. Lorsque vous cliquez avec le bouton droit pour lancer l’assistant, le serveur et la base de données sont déjà remplis automatiquement. S’il existe d’autres connexions actives, vous pouvez les sélectionner dans la liste déroulante. 
    
    Sélectionnez un fichier en cliquant sur **Parcourir**. Cela devrait remplir automatiquement le nom de la table en fonction du nom de fichier, mais vous pouvez également le modifier vous-même.

    Par défaut, le schéma est dbo, mais vous pouvez le modifier. Cliquez sur **Suivant** pour continuer.
    ![fichier d'entrée](media/sql-server-import-extension/import-wizard-input-file.png)
1. L’Assistant génère un aperçu basé sur les 50 premières lignes. Il n’y a pas d’action supplémentaire sur cette page, à l’exception de la vérification de l’exactitude des données. Cliquez sur **Suivant** pour continuer.
    ![ouvrir l’assistant d’importation](media/sql-server-import-extension/import-wizard-preview-data.png)
2. Sur cette page, vous pouvez modifier le nom de la colonne, le type de données, s’il s’agit d’une clé primaire ou autoriser les valeurs nulles. Vous pouvez apporter autant de modifications que vous le souhaitez. Cliquez sur **Importer des données** pour continuer.
    ![ouvrir l’assistant d’importation](media/sql-server-import-extension/import-wizard-modify-columns.png)
3. Cette page fournit un résumé des actions choisies. Vous pouvez également voir si votre table a été correctement insérée ou non. 

    Vous pouvez soit cliquer sur **Terminé, précédent** si vous devez apporter des modifications, soit **Importer un nouveau fichier** pour importer rapidement un autre fichier.
    ![ouvrir l’assistant d’importation](media/sql-server-import-extension/import-wizard-summary.png)
1. Vérifiez si votre table a été importée avec succès en actualisant votre base de données cible ou en exécutant une requête SELECT sur le nom de la table.

## <a name="next-steps"></a>Étapes suivantes
- Pour en savoir plus sur l’assistant importation, consultez ce [billet de blog](https://cloudblogs.microsoft.com/sqlserver/2018/08/30/the-august-release-of-sql-operations-studio-is-now-available/).
- Pour en savoir plus sur PROSE, consultez la [documentation.](https://microsoft.github.io/prose/)