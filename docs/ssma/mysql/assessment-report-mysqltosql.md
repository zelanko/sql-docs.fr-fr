---
title: Rapport d’évaluation (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 5525d989-024c-402d-9e84-faa4721cc5b9
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: fb6d01bf9c02d0a7b96adf8e46eb354cd426db4d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68139190"
---
# <a name="assessment-report-mysqltosql"></a>Rapport d’évaluation (MySQLToSQL)
La fenêtre rapport d’évaluation affiche les résultats de la conversion des objets de [!INCLUDE[tsql](../../includes/tsql-md.md)] base de données en syntaxe et peut également vous aider à estimer la complexité et le coût de vos projets de migration.  
  
Pour accéder au rapport d’évaluation, sélectionnez les objets à convertir dans l’Explorateur de métadonnées sources, cliquez avec le bouton droit sur **schémas**, puis sélectionnez **créer un rapport**.  
  
## <a name="options"></a>Options  
  
|||  
|-|-|  
|**Terme**|**Définition**|  
|**Statistiques de conversion**|Affiche les statistiques de conversion par type d’instruction. Ce volet est visible lorsqu’un objet de groupe, tel qu’un schéma, ou un objet sans code est sélectionné dans le volet gauche.|  
|**Objets par catégories**|Affiche le nombre d’objets par catégorie. Ce volet est visible uniquement lorsqu’un objet de groupe, tel qu’un schéma, ou un objet sans code est sélectionné dans le volet gauche.|  
|**Statistiques**|Affiche les statistiques de conversion pour l’objet sélectionné. Ce volet est visible uniquement lorsqu’un objet individuel avec code est sélectionné dans le volet gauche. Vous devrez peut-être développer les **statistiques**, qui est immédiatement au-dessus du volet **source** , pour afficher ce volet.|  
|**Source**|Affiche le code MySQL pour l’objet sélectionné et met en surbrillance le code qui [!INCLUDE[tsql](../../includes/tsql-md.md)]n’a pas été converti en. Ce volet est visible uniquement lorsqu’un objet individuel avec code est sélectionné dans le volet gauche.<br /><br />Cliquez sur les numéros de ligne pour définir ou supprimer des signets. Utilisez les boutons en haut du volet pour naviguer dans le code.|  
|**Indicatif**|Affiche le code résultant [!INCLUDE[tsql](../../includes/tsql-md.md)] de la conversion pour l’objet sélectionné, ainsi que les messages d’erreur pour le code qui n’a pas été converti. Ce volet est visible uniquement lorsqu’un objet individuel avec code est sélectionné dans le volet gauche.<br /><br />Cliquez sur les numéros de ligne pour définir ou supprimer des signets. Utilisez les boutons en haut du volet pour naviguer dans le code.|  
|**Volet Messages**|Affiche les erreurs, les avertissements et les messages d’information qui ont été générés lors de la création du rapport d’évaluation. Les messages sont regroupés par nombre. Pour afficher le code à l’origine de l’erreur, cliquez sur **Erreurs**, **avertissements**ou **informations**, développez la catégorie des messages, puis cliquez sur un message.|  
  
