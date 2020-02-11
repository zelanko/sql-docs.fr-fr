---
title: Boîte de dialogue Activer/désactiver l’écriture différée (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitiondesigner.writebackenabledisable.f1
ms.assetid: 2d254393-3f0d-4b70-8b98-87159f9f3639
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 498d1af6f96791b9ee3912c09a3667e139f30ff0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66081284"
---
# <a name="enable-disable-writeback-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Activer/désactiver l’écriture différée (Analysis Services-données multidimensionnelles)
  La boîte de dialogue **Activer/Désactiver l’écriture différée** permet d’activer ou de désactiver l’écriture différée pour un groupe de mesures dans un cube. L'activation de l'écriture différée dans un groupe de mesures définit une partition d'écriture différée et crée une table d'écriture différée pour le groupe de mesures. La désactivation de l'écriture différée dans un groupe de mesures supprime la partition d'écriture différée, mais ne supprime pas la table d'écriture différée pour éviter les pertes de données imprévues. Pour afficher la boîte de dialogue **Activer/Désactiver l’écriture différée** :  
  
-   Cliquez sur **Paramètres d’écriture différée** dans le volet **Groupes de mesures** de l’onglet **Partitions** du Concepteur de cube.  
  
-   Cliquez avec le bouton droit sur une partition dans la grille **Partitions** du volet **Groupes de mesures** sous l’onglet **Partitions** du Concepteur de cube et sélectionnez **Paramètres d’écriture différée** dans le menu contextuel.  
  
## <a name="options"></a>Options  
 **Nom de la table**  
 Tapez le nom de la table d'écriture différée à créer pour la partition sélectionnée. La table d’écriture différée stocke les modifications apportées au groupe de mesures par une application cliente.  
  
> [!NOTE]  
>  Cette option est désactivée si l'écriture différée n'est pas active.  
  
 **Source de données**  
 Sélectionne la source de données qui contiendra la table d'écriture différée.  
  
> [!NOTE]  
>  Cette option est désactivée si l'écriture différée n'est pas active.  
  
 **Nouveau**  
 Cliquez sur cette option pour afficher la boîte de dialogue **Gestionnaire de connexions** et définir une nouvelle source de données qui accueillera la table d’écriture différée.  
  
> [!NOTE]  
>  Cette option est désactivée si l'écriture différée n'est pas active.  
  
  
