---
title: SandDance pour Azure Data Studio
titleSuffix: Azure Data Studio
description: Comment utiliser SandDance dans Azure Data Studio
ms.custom: seodec18
ms.date: 07/03/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: a96bde6a66642bf02cc076c3d4d4f3ac44e02a3f
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959331"
---
# <a name="sanddance-for-azure-data-studio-preview"></a>SandDance pour Azure Data Studio (préversion)
Azure Data Studio offre désormais un moyen de créer des visualisations rapides pour les fichiers. csv et. tsv sur lesquels vous travaillez. Cela comprend les fichiers locaux ou les fichiers sur HDFS dans votre cluster Big Data SQL Server 2019. Cette extension est utile lorsque vous essayez d’examiner rapidement des données et de comprendre ce qui se passe. Nous utilisons une technologie appelée SandDance de Microsoft Research, qui peut générer des visualisations sur place des données.

![sanddance-animation](https://user-images.githubusercontent.com/11507384/54236654-52d42800-44d1-11e9-859e-6c5d297a46d2.gif)

Grâce à des vues faciles à comprendre, SandDance vous aide à trouver des informations sur vos données, qui à leur tour vous aideront à faire parler vos données, à créer des cas basés sur des preuves, à tester des idées, à approfondir les explications de surface, à prendre des décisions d’achat ou à lier les données dans un contexte de monde réel plus vaste.

SandDance utilise des visualisations d’unité, qui appliquent un mappage un-à-un entre les lignes de votre base de données et les marques sur l’écran.
Les transitions fluides animées entre les vues vous aident à maintenir le contexte lorsque vous interagissez avec vos données.

## <a name="usage"></a>Utilisation

À partir du menu Fichier, utilisez Ouvrir dossier ou [Ctrl+K Ctrl+O] pour ouvrir le répertoire contenant le fichier .CSV.  Ensuite, à partir du volet de l’explorateur, cliquez avec le bouton droit sur le fichier .csv ou .tsv, puis choisissez *Afficher dans SandDance*.

Cliquez avec le bouton droit sur un fichier. csv ou .tsv dans HDFS si vous êtes connecté à un cluster Big Data SQL Server 2019, puis choisissez *Afficher dans SandDance*.

## <a name="known-issues"></a>Problèmes connus

Actuellement, vos données doivent avoir un identificateur unique dans la première colonne.

Actuellement, nous ne limitons pas le nombre de lignes visualisées. Toutefois, la consommation de mémoire augmente proportionnellement au nombre de lignes ; nous vous recommandons donc de limiter le jeu de données ou la vue à environ 100 000 lignes.

Consulter les [problèmes connus](https://microsoft.github.io/SandDance/#known-issues)

## <a name="release-notes"></a>Notes de publication

### <a name="100"></a>1.0.0

Version initiale d’azdata-sanddance

## <a name="next-steps"></a>Next Steps
Pour en savoir plus, [visitez le référentiel GitHub.](https://github.com/Microsoft/SandDance)
