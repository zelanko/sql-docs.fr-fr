---
title: Installer des versions antérieures de la documentation SQL Server hors connexion
description: Découvrez comment installer la documentation hors connexion pour SQL Server 2019, 2017, 2016, 2014 et 2012. Utilisez SQL Server Management Studio (SSMS) pour afficher le contenu hors connexion.
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
author: markingmyname
ms.author: maghan
ms.date: 04/20/2020
ms.openlocfilehash: 1420e18fbf335e22d44bf78d526ab35c8b1434e5
ms.sourcegitcommit: c37777216fb8b464e33cd6e2ffbedb6860971b0d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82087869"
---
# <a name="install-previous-versions-of-sql-server-documentation-to-view-offline-in-ssms"></a>Installer des versions antérieures de la documentation SQL Server pour un affichage hors connexion dans SSMS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article explique comment télécharger et afficher le contenu SQL Server hors connexion dans [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md). Le contenu hors connexion vous permet d’accéder à la documentation sans connexion Internet (bien qu’une connexion Internet soit initialement requise pour le téléchargement).

La documentation hors connexion est disponible pour plusieurs versions précédentes de SQL Server. Bien que vous puissiez également [afficher le contenu des versions précédentes en ligne](https://docs.microsoft.com/previous-versions/sql/), une option hors connexion offre un moyen pratique d’accéder à l’ancien contenu.

## <a name="how-to-download-and-configure-offline-content"></a>Comment télécharger et configurer le contenu hors connexion

Vous pouvez télécharger et installer les packages d’aide SQL Server à partir de sources en ligne ou du disque local. Les sections suivantes expliquent comment charger du contenu hors connexion pour différentes versions de SQL Server :

- [SQL Server 2019](#sql2019)
- [SQL Server 2017](#sql2017)
- [SQL Server 2016](#sql2016)
- [SQL Server 2014](#sql2014)
- [SQL Server 2012](#sql2012)

## <a name="sql-server-2019"></a><a id="sql2019"></a> SQL Server 2019

Procédez comme suit pour charger la documentation hors connexion pour SQL Server 2019.

1. Dans SSMS, sélectionnez **Ajouter et supprimer le contenu d’aide** dans le menu Aide.

   ![Visionneuse d’aide - Ajouter et supprimer le contenu](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   La visionneuse d’aide s’ouvre et affiche l’onglet Gérer le contenu.

2. Pour trouver le contenu d’aide le plus récent pour SQL Server 2019, sous l’onglet **Gérer le contenu** choisissez **En ligne** sous Source d’installation, puis saisissez *SQL Server 2019* dans la barre de recherche.

   ![Recherche de documentation de SQL Server 2019 dans la visionneuse d’aide](../sql-server/media/sql-server-help-installation/sql-2019-search.png)

   > [!Note]
   > L’option Chemin d’accès au stockage local sous l’onglet Gérer le contenu indique l’emplacement sur l’ordinateur local où est installé le contenu. Pour changer d’emplacement, sélectionnez **Déplacer**, entrez un chemin de dossier différent dans le champ **Vers**, puis sélectionnez **OK**. Si l’installation de l’aide échoue après avoir modifié le chemin d’accès du magasin local, fermez et rouvrez la visionneuse d’aide. Vérifiez que le nouvel emplacement apparaît dans le chemin d’accès du magasin local, puis recommencez l’installation.

3. Pour installer le contenu d’aide le plus récent pour SQL Server 2019, sélectionnez **Ajouter** en regard de chaque package de contenu (livre) que vous souhaitez installer, puis sélectionnez **Mettre à jour** dans le coin inférieur droit.

   ![Livres SQL Server 2019 - Ajouter et mettre à jour dans la visionneuse d’aide](../sql-server/media/sql-server-help-installation/sql-2019-add-update.png)

   > [!NOTE]
   > Si la visionneuse d’aide se fige (se bloque) pendant l’ajout du contenu, remplacez la ligne Dernière actualisation du cache = « \<jj/mm/aaaa> 00:00:00 » dans le fichier %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings ou HlpViewer_VisualStudiox_en-US.settings par une date dans le futur. Pour plus d’informations sur ce problème, consultez [La visionneuse d’aide Visual Studio se fige sur l’écran de démarrage](/visualstudio/welcome-to-visual-studio).

4. Vous pouvez vérifier que le contenu SQL Server 2019 est chargé en effectuant une recherche dans le volet de contenu à gauche pour *SQL Server 2019*.

   ![Livres SQL Server 2019 automatiquement mis à jour](../sql-server/media/sql-server-help-installation/sql-2019-content.png)

## <a name="sql-server-2017"></a><a id="sql2017"></a> SQL Server 2017

Procédez comme suit pour charger la documentation hors connexion pour SQL Server 2017.

1. Dans SSMS, sélectionnez **Ajouter et supprimer le contenu d’aide** dans le menu Aide.

   ![Visionneuse d’aide - Ajouter et supprimer le contenu](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   La visionneuse d’aide s’ouvre et affiche l’onglet Gérer le contenu.

2. Pour trouver le contenu d’aide le plus récent pour SQL Server 2017, sous l’onglet **Gérer le contenu** choisissez **En ligne** sous Source d’installation, puis saisissez *SQL Server 2017* dans la barre de recherche.

   ![Recherche de livres SQL Server 2017 dans la visionneuse d’aide](../sql-server/media/sql-server-help-installation/sql-2017-search.png)

   > [!Note]
   > L’option Chemin d’accès au stockage local sous l’onglet Gérer le contenu indique l’emplacement sur l’ordinateur local où est installé le contenu. Pour changer d’emplacement, sélectionnez **Déplacer**, entrez un chemin de dossier différent dans le champ **Vers**, puis sélectionnez **OK**. Si l’installation de l’aide échoue après avoir modifié le chemin d’accès du magasin local, fermez et rouvrez la visionneuse d’aide. Vérifiez que le nouvel emplacement apparaît dans le chemin d’accès du magasin local, puis recommencez l’installation.

3. Pour installer le contenu d’aide le plus récent pour SQL Server 2017, sélectionnez **Ajouter** en regard de chaque package de contenu (livre) que vous souhaitez installer, puis sélectionnez **Mettre à jour** dans le coin inférieur droit.

   ![Livres SQL Server 2017 - Ajouter et mettre à jour dans la visionneuse d’aide](../sql-server/media/sql-server-help-installation/sql-2017-add-update.png)

   > [!NOTE]
   > Si la visionneuse d’aide se fige (se bloque) pendant l’ajout du contenu, remplacez la ligne Dernière actualisation du cache = « \<jj/mm/aaaa> 00:00:00 » dans le fichier %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings ou HlpViewer_VisualStudiox_en-US.settings par une date dans le futur. Pour plus d’informations sur ce problème, consultez [La visionneuse d’aide Visual Studio se fige sur l’écran de démarrage](/visualstudio/welcome-to-visual-studio).

4. Vous pouvez vérifier que le contenu SQL Server 2017 est chargé en effectuant une recherche dans le volet de contenu à gauche pour *SQL Server 2017*.

   ![Livres SQL Server 2017 automatiquement mis à jour](../sql-server/media/sql-server-help-installation/sql-2017-content.png)

## <a name="sql-server-2016"></a><a id="sql2016"></a> SQL Server 2016

Procédez comme suit pour charger la documentation hors connexion pour SQL Server 2016.

1. Dans SSMS, sélectionnez **Ajouter et supprimer le contenu d’aide** dans le menu Aide.

   ![Visionneuse d’aide - Ajouter et supprimer le contenu](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   La visionneuse d’aide s’ouvre et affiche l’onglet Gérer le contenu.

2. Pour trouver le contenu d’aide le plus récent pour SQL Server 2016, sous l’onglet **Gérer le contenu** choisissez **En ligne** sous Source d’installation, puis saisissez *SQL Server 2016* dans la barre de recherche.

   ![Recherche de livres SQL Server 2016 dans la visionneuse d’aide](../sql-server/media/sql-server-help-installation/sql-2016-search.png)

   > [!Note]
   > L’option Chemin d’accès au stockage local sous l’onglet Gérer le contenu indique l’emplacement sur l’ordinateur local où est installé le contenu. Pour changer d’emplacement, sélectionnez **Déplacer**, entrez un chemin de dossier différent dans le champ **Vers**, puis sélectionnez **OK**. Si l’installation de l’aide échoue après avoir modifié le chemin d’accès du magasin local, fermez et rouvrez la visionneuse d’aide. Vérifiez que le nouvel emplacement apparaît dans le chemin d’accès du magasin local, puis recommencez l’installation.

3. Pour installer le contenu d’aide le plus récent pour SQL Server 2016, sélectionnez **Ajouter** en regard de chaque package de contenu (livre) que vous souhaitez installer, puis sélectionnez **Mettre à jour** dans le coin inférieur droit.

   ![Livres SQL Server 2016 - Ajouter et mettre à jour dans la visionneuse d’aide](../sql-server/media/sql-server-help-installation/sql-2016-add-update.png)

   > [!NOTE]
   > Si la visionneuse d’aide se fige (se bloque) pendant l’ajout du contenu, remplacez la ligne Dernière actualisation du cache = « \<jj/mm/aaaa> 00:00:00 » dans le fichier %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings ou HlpViewer_VisualStudiox_en-US.settings par une date dans le futur. Pour plus d’informations sur ce problème, consultez [La visionneuse d’aide Visual Studio se fige sur l’écran de démarrage](/visualstudio/welcome-to-visual-studio).

4. Vous pouvez vérifier que le contenu SQL Server 2016 est chargé en effectuant une recherche dans le volet de contenu à gauche pour *SQL Server 2016*.

   ![Livres SQL Server 2016 automatiquement mis à jour](../sql-server/media/sql-server-help-installation/sql-2016-content.png)

## <a name="sql-server-2014"></a><a id="sql2014"></a> SQL Server 2014

Procédez comme suit pour charger la documentation hors connexion pour SQL Server 2014.

1. Téléchargez la [documentation produit pour Microsoft SQL Server 2014 pour les environnements protégés par un pare-feu restreints par un proxy](https://www.microsoft.com/download/details.aspx?id=42557) à partir du centre de téléchargement et enregistrez-la dans un dossier.

2. Décompressez le fichier pour voir le fichier .msha.

   ![Fichier d’installation de la documentation d’aide de SQL Server 2014](../sql-server/media/sql-server-help-installation/sql-2014-help-content-setup-msha.png)

3. Dans SSMS, sélectionnez **Ajouter et supprimer le contenu d’aide** dans le menu Aide.

   ![HelpViewer - Ajouter et supprimer le contenu](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   La visionneuse d’aide s’ouvre et affiche l’onglet Gérer le contenu.

4. Pour installer le contenu d’aide le plus récent, choisissez **Disque** sous Source d’installation, puis cliquez sur les points de suspension (...).

   ![Visionneuse d’aide - Gérer la source du disque de contenu](../sql-server/media/sql-server-help-installation/install-source-disk.png)

   > [!NOTE]
   > L’option Chemin d’accès au stockage local sous l’onglet Gérer le contenu indique l’emplacement sur l’ordinateur local où est situé le contenu. Pour changer d’emplacement, sélectionnez **Déplacer**, entrez un chemin de dossier différent dans le champ **Vers**, puis sélectionnez **OK**.
   Si l’installation de l’aide échoue après avoir modifié le chemin d’accès du magasin local, fermez et rouvrez la visionneuse d’aide. Vérifiez que le nouvel emplacement apparaît dans le chemin d’accès du magasin local, puis recommencez l’installation.

5. Localisez le dossier dans lequel vous avez décompressé le contenu. Sélectionnez le fichier **HelpContentSetup.msha** dans le dossier, puis sélectionnez **Ouvrir**.

   ![Ouvrir le fichier d’aide de SQL Server 2014 Setup.msha](../sql-server/media/sql-server-help-installation/sql-2014-open-msha.png)

6. Saisissez *SQL Server 2014* dans la barre de recherche. Une fois que vous voyez le contenu 2014 disponible, sélectionnez **Ajouter** en regard de chaque package de contenu (livre) que vous souhaitez installer dans la visionneuse d’aide, puis sélectionnez **Mettre à jour**.

   ![Recherche de livres SQL Server 2014 dans la visionneuse d’aide](../sql-server/media/sql-server-help-installation/sql-2014-search.png)

   ![Livres SQL Server 2014 - Ajouter et mettre à jour dans la visionneuse d’aide](../sql-server/media/sql-server-help-installation/sql-2014-add-update.png)

    > [!NOTE]
    > Si la visionneuse d’aide se fige (se bloque) pendant l’ajout du contenu, remplacez la ligne Dernière actualisation du cache = « \<jj/mm/aaaa> 00:00:00 » dans le fichier %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings ou HlpViewer_VisualStudiox_en-US.settings par une date dans le futur. Pour plus d’informations sur ce problème, consultez [La visionneuse d’aide Visual Studio se fige sur l’écran de démarrage](/visualstudio/welcome-to-visual-studio).

7. Vous pouvez vérifier que le contenu SQL Server 2014 est installé en effectuant une recherche dans le volet de contenu à gauche pour *SQL Server 2014*.

   ![Livres SQL Server 2014 automatiquement mis à jour](../sql-server/media/sql-server-help-installation/sql-2014-content.png)

## <a name="sql-server-2012"></a><a id="sql2012"></a> SQL Server 2012

Procédez comme suit pour charger la documentation hors connexion pour SQL Server 2012.

1. Téléchargez la [documentation produit pour Microsoft SQL Server 2012 pour les environnements protégés par un pare-feu restreints par un proxy](https://www.microsoft.com/download/details.aspx?id=35750) à partir du centre de téléchargement et enregistrez-la dans un dossier.

2. Décompressez le fichier pour voir le fichier .msha.

   ![Fichier d’installation du contenu de l’aide SQL Server 2012](../sql-server/media/sql-server-help-installation/sql-2012-help-content-setup-msha.png)

3. Dans SSMS, sélectionnez **Ajouter et supprimer le contenu d’aide** dans le menu Aide.

   ![HelpViewer - Ajouter et supprimer le contenu](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   La visionneuse d’aide s’ouvre et affiche l’onglet Gérer le contenu.

4. Pour installer le contenu d’aide le plus récent, choisissez **Disque** sous Source d’installation, puis cliquez sur les points de suspension (...).

   ![Visionneuse d’aide - Gérer la source du disque de contenu](../sql-server/media/sql-server-help-installation/install-source-disk.png)

   > [!NOTE]
   > L’option Chemin d’accès au stockage local sous l’onglet Gérer le contenu indique l’emplacement sur l’ordinateur local où est situé le contenu. Pour changer d’emplacement, sélectionnez **Déplacer**, entrez un chemin de dossier différent dans le champ **Vers**, puis sélectionnez **OK**.
   Si l’installation de l’aide échoue après avoir modifié le chemin d’accès du magasin local, fermez et rouvrez la visionneuse d’aide. Vérifiez que le nouvel emplacement apparaît dans le chemin d’accès du magasin local, puis recommencez l’installation.

5. Localisez le dossier dans lequel vous avez décompressé le contenu. Sélectionnez le fichier **HelpContentSetup.msha** dans le dossier, puis sélectionnez **Ouvrir**.

   ![Ouvrir le fichier d’aide de SQL Server 2012 Setup.msha](../sql-server/media/sql-server-help-installation/sql-2012-open-msha.png)

6. Saisissez *SQL Server 2012* dans la barre de recherche. Une fois que vous voyez le contenu 2012 disponible, sélectionnez **Ajouter** en regard de chaque package de contenu (livre) que vous souhaitez installer dans la visionneuse d’aide, puis sélectionnez **Mettre à jour**.

   ![Recherche de livres SQL Server 2012 dans la visionneuse d’aide](../sql-server/media/sql-server-help-installation/sql-2012-search.png)

   ![Livres SQL Server 2012 - Ajouter et mettre à jour dans la visionneuse d’aide](../sql-server/media/sql-server-help-installation/sql-2012-add-update.png)

    > [!NOTE]
    > Si la visionneuse d’aide se fige (se bloque) pendant l’ajout du contenu, remplacez la ligne Dernière actualisation du cache = « \<jj/mm/aaaa> 00:00:00 » dans le fichier %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings ou HlpViewer_VisualStudiox_en-US.settings par une date dans le futur. Pour plus d’informations sur ce problème, consultez [La visionneuse d’aide Visual Studio se fige sur l’écran de démarrage](/visualstudio/welcome-to-visual-studio).

7. Vous pouvez vérifier que le contenu SQL Server 2012 est chargé en effectuant une recherche dans le volet de contenu à gauche pour *SQL Server 2012*.

   ![Documentation SQL Server 2012 mise à jour automatiquement](../sql-server/media/sql-server-help-installation/sql-2012-content.png)

## <a name="view-offline-documentation"></a>Voir la documentation hors connexion

Vous pouvez afficher le contenu de l’aide de SQL Server dans le menu **AIDE** de la dernière version de [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md).

### <a name="view-offline-help-content-in-ssms"></a>Afficher le contenu de l’aide hors connexion dans SSMS

Pour afficher l’aide installée dans SSMS, sélectionnez **Lancer dans la visionneuse d’aide** dans le menu Aide, afin de lancer la visionneuse d’aide.

   ![Lancer dans la visionneuse d’aide](../sql-server/media/sql-server-help-installation/helpviewer-view-offline.png)  

La visionneuse d’aide s’ouvre et affiche l’onglet Gérer le contenu, avec la table des matières de l’aide installée dans le volet gauche. Sélectionnez les articles dans la table des matières pour les afficher dans le volet droit.

> [!TIP]
> Si le volet de contenu n’est pas visible, sélectionnez Contenu dans la marge gauche. Sélectionnez l’icône représentant une punaise pour garder le volet de contenu ouvert.  

   ![Visionneuse d’aide avec du contenu](../sql-server/media/sql-server-help-installation/view-offline-all.png)

## <a name="life-cycle-policy"></a>Stratégie de cycle de vie

Consultez le cycle de vie des produits Microsoft pour plus d’informations sur la prise en charge d’un produit, d’un service ou d’une technologie spécifique :

- [Stratégie de cycle de vie Microsoft](https://support.microsoft.com/lifecycle/selectindex)

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur le contenu archivé et sur la visionneuse d’aide, reportez-vous aux liens ci-dessous.

- [Lien direct vers les versions précédentes de la documentation SQL Server](https://docs.microsoft.com/previous-versions/sql/)
- [Microsoft Help Viewer - Visual Studio](https://docs.microsoft.com/visualstudio/help-viewer/overview)
- [Documentation SQL Server, bien démarrer](../sql-server/index.yml?view=sql-server-2016)
- [Système de gestion des versions dans la documentation SQL](../sql-server/versioning-system-monikers-ui-sql-server.md?view=sql-server-2016)