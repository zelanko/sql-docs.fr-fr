---
title: 'Leçon 1 : Création de la Base de connaissances DQS nommée fournisseurs | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 78825ccb-30fc-463c-8140-435532e2ecd2
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 6e25b57bce84876de1119ec52ad068602cd5cf13
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65485591"
---
# <a name="lesson-1-creating-the-suppliers-dqs-knowledge-base"></a>Leçon 1 : Création d’une base de connaissances DQS nommée Fournisseurs
  Dans cette leçon, vous créez une base de connaissances DQS nommée **fournisseurs** avec la base de connaissances (métadonnées) sur les données des fournisseurs. Utilisez la base de connaissances pour effectuer les activités de nettoyage et de correspondance sur les données d'entrée des fournisseurs. L'activité de nettoyage identifie les données incorrectes ou non valides, les corrige, propose des corrections/suggestions, normalise les données, et les enrichit avec des informations. L'activité de correspondance compare les données et identifie les enregistrements de données similaires (mais légèrement différents), et vous permet de supprimer les doublons.  
  
 Vous pouvez utiliser des processus assistés par ordinateur et interactifs pour créer et gérer une base de connaissances. Les connaissances contenues dans une base de connaissances sont conservées dans des domaines, chacun d'entre eux étant spécifique à un champ dans les données que vous souhaitez nettoyer et/ou mettre en correspondance.  
  
 Dans cette leçon, vous procédez comme suit pour créer le **fournisseurs** base de connaissances :  
  
-   Créer une base de connaissances DQS nommée **fournisseurs**. Vous pouvez créer une base de connaissances de différentes façons. Vous pouvez créer une base de connaissances de toutes pièces ou à partir d'une base de connaissances existante, ou encore, vous pouvez importer un fichier DQS (.dqs) contenant une base de connaissances prégénérée et exportée, ou exécuter une activité de découverte de connaissances sur un échantillon de données. Dans ce didacticiel, vous allez créer une base de connaissances de toutes pièces.  
  
-   Créer des domaines dans le **fournisseurs** base de connaissances que vous utiliser pour nettoyer les données et les données correspondantes pour identifier les doublons. Créez des domaines pour les champs de données que vous souhaitez utiliser pour nettoyer les données et les mettre en correspondance, mais pas pour tous les champs de données dans les données.  
  
-   Ajouter des valeurs à un domaine manuellement, importer des valeurs à partir d'un fichier Excel, effectuer une activité de découverte des connaissances sur un échantillon de données, ou importer des valeurs de projet depuis un projet de nettoyage. Vous pouvez également importer des valeurs de domaine en important un fichier DQS qui contient des propriétés et des valeurs de champ, cependant, cette procédure n'est pas décrite dans le didacticiel.  
  
-   Définir les règles pour un domaine. Une règle de domaine est une condition utilisée par DQS pour valider, corriger et normaliser les valeurs de domaine.  
  
-   Définir des relations à base de termes pour un domaine. Une relation à base de termes vous permet d'effectuer une correction sur un terme qui fait partie d'une valeur dans un domaine. Par exemple, dans la valeur **Contoso Inc., Inc.** est un terme qui peut être défini comme « Incorporated ». Une telle approche permet de normaliser les données et d'identifier les doublons. Par exemple, **Contoso Inc.** et **Contoso Incorporated** peuvent être considérés comme des doublons.  
  
-   Spécifier les synonymes dans les valeurs de domaine. Vous pouvez définir deux valeurs ou plus comme étant des synonymes et configurer l'une d'entre elles comme valeur menante, pouvant remplacer les synonymes lors d'une activité de nettoyage, afin de normaliser les données.  
  
-   Créer un domaine composite nommé Validation d'adresses incluant les domaines Adresse, Ville, État et Code postal. Un domaine composite est un domaine qui comprend un ou plusieurs domaines individuels. Il vous permet de créer une règle impliquant plusieurs domaines. Par exemple, si vous avez défini une règle : si Ville est Los Angeles, État doit être CA (pour Californie), où Ville et État sont deux domaines différents.  
  
-   Configurer et utiliser un service de données de référence. Dans Data Quality Services (DQS), la fonctionnalité de service de données de référence vous permet de vous abonner à des fournisseurs de données de référence tiers, et nettoyer et enrichir facilement vos données métier en les validant par rapport à des données de grande qualité. Vous pouvez utiliser les services des meilleurs fournisseurs DQS à partir de DQS, afin de normaliser, corriger ou enrichir vos données pendant le processus de nettoyage. Dans ce didacticiel, vous allez configurer votre environnement DQS pour utiliser un service de données de référence dans la Place de marché Microsoft Azure, et pour utiliser le service associé au domaine composite Validation d'adresses pour nettoyer les données d'adresse.  
  
-   Publiez la base de connaissances afin qu'elle puisse être utilisée pour les activités de nettoyage et de correspondance.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 1 : Création d’une Base de connaissances et domaines](../../2014/tutorials/task-1-creating-a-knowledge-base-and-domains.md)  
  
  
