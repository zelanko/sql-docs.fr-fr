---
title: Extension d’importation SQL Server
titleSuffix: Azure Data Studio
description: Installer et utiliser l’extension de SQL Server Import (version préliminaire) pour Azure Data Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 012c2c880e81c095e90086cf26ebffd6117d534e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959122"
---
# <a name="sql-server-import-extension-preview"></a>Extension de SQL Server Import (version préliminaire)

L’extension de SQL Server Import (version préliminaire) convertit les fichiers .txt et .csv dans une table SQL. Cet Assistant utilise un framework de Microsoft Research appelé [Program Synthesis using exemples (PROSE)](https://microsoft.github.io/prose/) intelligemment analyser le fichier avec une entrée utilisateur minimale. Il est un framework puissant pour la transformation préalable des données, et il est la même technologie qui alimente Flash remplir dans Microsoft Excel

Pour en savoir plus sur la version SSMS de cette fonctionnalité, vous pouvez lire [cet article](https://docs.microsoft.com/sql/relational-databases/import-export/import-flat-file-wizard).


## <a name="install-the-sql-server-import-extension"></a>Installer l’extension de SQL Server Import

1. Pour ouvrir le Gestionnaire d’extensions et accéder aux extensions disponibles, sélectionnez l’icône des extensions ou **Extensions** dans le **vue** menu.
2. Sélectionner une extension disponible pour afficher ses détails.

   ![importer le Gestionnaire d’extensions](media/sql-server-import-extension/import-wizard-install.png)

1. Sélectionnez l’extension souhaitée et **installer** il.
2. Sélectionnez **recharger** pour activer l’extension (uniquement obligatoire la première fois que vous installez une extension).

## <a name="start-import-wizard"></a>Démarrez l’Assistant Importation

1. Pour démarrer SQL Server Import, vous devez tout d’abord établir une connexion à un serveur dans l’onglet serveurs.
2. Après avoir établi une connexion, accédez à la base de données cible que vous souhaitez importer un fichier dans une table SQL.
3. Avec le bouton droit sur la base de données et cliquez sur **Assistant importation**.
    ![Assistant Importation ouvert](media/sql-server-import-extension/open-import-wizard.png)

## <a name="importing-a-file"></a>Importation d’un fichier
1. Lorsque vous cliquez sur pour lancer l’Assistant, le serveur et la base de données sont déjà renseignées automatiquement. S’il existe d’autres connexions actives, vous pouvez sélectionner dans la liste déroulante. 
    
    Sélectionnez un fichier en cliquant sur **Parcourir.** Il doit le remplissage automatique du nom de la table en fonction du nom de fichier, mais vous pouvez également le modifier vous-même.

    Par défaut, le schéma sera dbo, mais vous pouvez le modifier. Cliquez sur **Suivant** pour continuer.
    ![fichier d’entrée](media/sql-server-import-extension/import-wizard-input-file.png)
1. L’Assistant génère une version d’évaluation basée sur les 50 premières lignes. Aucune action n’est plue sur cette page autres que la vérification des que données recherche précises. Cliquez sur **Suivant** pour continuer.
    ![Assistant Importation ouvert](media/sql-server-import-extension/import-wizard-preview-data.png)
2. Dans cette page, vous pouvez apporter des modifications au nom de colonne, type de données, si elle est une clé primaire, ou pour autoriser les valeurs NULL. Vous pouvez apporter autant de modifications que vous le souhaitez. Cliquez sur **importer des données** pour continuer.
    ![Assistant Importation ouvert](media/sql-server-import-extension/import-wizard-modify-columns.png)
3. Cette page fournit un résumé des actions choisi. Vous pouvez également voir si votre table inséré avec succès ou non. 

    Vous pouvez cliquer sur **terminé, précédent** si vous avez besoin apporter des modifications, ou **nouveau fichier d’importation** pour importer rapidement un autre fichier.
    ![Assistant Importation ouvert](media/sql-server-import-extension/import-wizard-summary.png)
1. Vérifiez si votre table importée avec succès par l’actualisation de votre base de données cible ou en exécutant une requête SELECT sur le nom de table.

## <a name="next-steps"></a>Étapes suivantes
- Pour en savoir plus sur l’Assistant Importation, lisez le [billet de blog](https://cloudblogs.microsoft.com/sqlserver/2018/08/30/the-august-release-of-sql-operations-studio-is-now-available/).
- Pour en savoir plus sur PROSE, lisez le [documentation.](https://microsoft.github.io/prose/)
