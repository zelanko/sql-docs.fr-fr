---
title: Requête d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquery.f1
ms.assetid: 948e358a-6245-429f-82c7-4cedc5e048fd
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 07373f17838fa387fe6ee22e31312a3933307fa3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68890328"
---
# <a name="data-mining-query"></a>Requête d'exploration de données
  Le volet de conception contient le Générateur de requêtes de prévisions d'exploration de données, qui peut servir à créer des requêtes de prévisions d'exploration de données. Vous pouvez concevoir des requêtes de prévisions basées sur des tables d'entrée ou des requêtes de prévisions singleton. Passez à la vue de résultat pour exécuter la requête et afficher les résultats. La vue de la requête affiche la requête DMX (Data Mining Extensions) créée par le Générateur de requêtes de prévisions d'exploration de données.  
  
## <a name="options"></a>Options  
 Bouton de basculement entre les vues  
 Cliquez sur une icône pour basculer entre le volet de conception et le volet de requête. Par défaut, le volet de conception est ouvert.  
  
 Pour basculer vers le volet de conception, cliquez sur l’icône ![icône de conception](../media/ssis-designicon.gif "Icône de conception") .  
  
 Pour basculer vers le volet de requête, cliquez sur l’icône de l' ![icône SQL](../media/ssis-queryicon.gif "Icône SQL") .  
  
 **Modèle d’exploration de données**  
 Choisissez le modèle d'exploration de données sur lequel vous souhaitez baser vos prévisions.  
  
 **Sélectionner un modèle**  
 Ouvre la boîte de dialogue **Sélectionnez un modèle d’exploration de données** .  
  
 **Colonnes d’entrée**  
 Affiche les colonnes d'entrée sélectionnées utilisées pour générer les prévisions.  
  
 **Source**  
 Sélectionnez dans la liste déroulante la source contenant le champ qui sera utilisé pour la colonne. Vous pouvez utiliser le modèle d’exploration de données sélectionné dans la table **Modèle d’exploration de données** , la ou les tables d’entrée sélectionnées dans la table **Sélectionner une ou plusieurs tables d’entrée** , une fonction de prédiction ou une expression personnalisée.  
  
 Les colonnes des tables contenant le modèle d'exploration de données et les colonnes d'entrée peuvent être glissées et déplacées sur la cellule.  
  
 **Champ**  
 Sélectionnez une colonne dans la liste des colonnes dérivées de la table source. Si vous avez sélectionné **Fonction de prédiction** dans **Source**, cette cellule contient une liste déroulante des fonctions de prédiction disponibles pour le modèle d’exploration de données sélectionné.  
  
 **Alias**  
 Nom de la colonne retourné par le serveur.  
  
 **Afficher**  
 Sélectionnez cette option pour retourner la colonne ou pour utiliser la colonne uniquement dans la clause WHERE.  
  
 **Groupe**  
 Utilisez cette option avec la colonne **et/ou** pour regrouper les expressions. Par exemple, (expr1 OU expr2) ET expr3.  
  
 **Et/ou**  
 Utilisez cette option pour créer une requête logique. Par exemple, (expr1 OU expr2) ET expr3.  
  
 **Critères/argument**  
 Spécifiez une condition ou une expression utilisateur qui s'applique à la colonne. Les colonnes des tables contenant le modèle d'exploration de données et les colonnes d'entrée peuvent être glissées et déplacées sur la cellule.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de requête d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](/sql/dmx/data-mining-extensions-dmx-statements)  
  
  
