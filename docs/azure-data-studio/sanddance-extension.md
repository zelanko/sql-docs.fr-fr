---
title: SandDance pour Azure Data Studio
titleSuffix: Azure Data Studio
description: Comment utiliser SandDance dans Azure Data Studio
ms.custom: seodec18
ms.date: 04/18/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 8fe968185f05c7a48415e5e158a20f4dc61b28c1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63142191"
---
# <a name="sanddance-for-azure-data-studio-preview"></a>SandDance pour Azure Data Studio (version préliminaire)
Azure Data Studio offre désormais un moyen de créer des visualisations rapides pour les fichiers .csv, .tsv que vous utilisez. Cela inclut les fichiers locaux ou des fichiers sur HDFS dans votre Cluster SQL Server 2019 Big Data. Cette extension est utile lorsque vous essayez d’avoir un rapide aperçu des données et de comprendre ce qui se passe. Nous utilisons une technologie appelée SandDance de Microsoft Research, ce qui peut générer des visualisations sur place des données.

![sanddance-animation](https://user-images.githubusercontent.com/11507384/54236654-52d42800-44d1-11e9-859e-6c5d297a46d2.gif)

À l’aide de vues faciles à comprendre, vous permet de SandDance rechercher insights sur vos données, qui, dans l’aide de tour parler est pris en charge par les données, générer des cas basées sur la preuve, tester des hypothèses, aller plus loin dans l’aire de conception explications, prennent en charge des décisions d’achats, ou lier des données dans un contexte plus large, dans la réalité.

SandDance utilise des visualisations d’unité, qui s’appliquent un mappage entre les lignes dans votre base de données et les marques sur l’écran.
Transitions animées sans heurts entre les vues vous aident à maintenir le contexte lorsque vous interagissez avec vos données.

## <a name="usage"></a>Utilisation

À partir du menu fichier, permet d’ouvrir le dossier ou [Ctrl + K, Ctrl + O] pour ouvrir le répertoire contenant le. Fichier CSV.  Ensuite, à partir de dans le volet Explorateur, avec le bouton droit sur le fichier .csv ou .tsv, choisissez *vue dans SandDance*.

Avec le bouton droit sur un fichier .csv ou .tsv dans HDFS si vous êtes connecté à SQL Server 2019 Big Data Cluster et choisissez *vue dans SandDance*.

## <a name="known-issues"></a>Problèmes connus

Actuellement vos données doivent avoir la première colonne comme identificateur unique.

Actuellement nous ne pas limiter le nombre de lignes est affiché. Toutefois, la consommation de mémoire augmente proportionnellement au nombre de lignes, nous recommandons que le jeu de données ou la vue est limitée à environ 100 lignes de k.

Consultez [problèmes connus](https://microsoft.github.io/SandDance/#known-issues)

## <a name="release-notes"></a>Notes de publication

### <a name="100"></a>1.0.0

Version initiale d’azdata-sanddance

## <a name="next-steps"></a>Étapes suivantes
Pour en savoir plus, [visitez le référentiel GitHub.](https://github.com/Microsoft/SandDance)
