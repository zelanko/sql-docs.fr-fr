---
title: Rapport d’évaluation (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: af24f2c4-5e86-4135-a4f3-a24faaeeefe7
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c6d83e81253430f243fcaed55b66f6d0de6299ca
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68083505"
---
# <a name="assessment-report-sybasetosql"></a>Rapport d’évaluation (SybaseToSQL)
La fenêtre de rapport d’évaluation affiche les résultats de la conversion d’objets de base de données à [!INCLUDE[tsql](../../includes/tsql-md.md)] syntaxe, et peut également aider à vous estimer le coût et complexité de vos projets de migration.  
  
Pour accéder au rapport d’évaluation, sélectionner les objets à convertir dans l’Explorateur de métadonnées de source, avec le bouton droit **bases de données**, puis sélectionnez **créer un rapport**.  
  
## <a name="options"></a>Options  
**Statistiques de conversion**  
Affiche les statistiques de la conversion en type d’instruction. Ce volet est visible uniquement lorsqu’un objet de groupe, tel qu’un schéma, ou un objet sans code est sélectionné dans le volet gauche.  
  
**Objets par catégorie**  
Affiche les statistiques de la conversion en type d’objet. Ce volet est visible uniquement lorsqu’un objet de groupe, tel qu’un schéma, ou un objet sans code est sélectionné dans le volet gauche.  
  
**Statistiques**  
Affiche les statistiques de conversion de l’objet sélectionné. Ce volet est visible uniquement lorsqu’un objet avec le code est sélectionné dans le volet gauche. Vous devrez peut-être développer **statistiques** pour afficher ce volet.  
  
**Navigation vers la source**  
Affiche le code de l’ASE pour l’objet sélectionné et met en évidence de code qui n’a pas été converti à [!INCLUDE[tsql](../../includes/tsql-md.md)]. Ce volet est visible uniquement lorsqu’un objet avec le code est sélectionné dans le volet gauche.  
  
Cliquez sur les numéros de ligne pour définir ou supprimer des signets. Utilisez les boutons en haut du volet pour naviguer dans le code.  
  
**Navigation de la cible**  
Montre la conversion du résultant [!INCLUDE[tsql](../../includes/tsql-md.md)] code pour l’objet sélectionné et les messages d’erreur pour le code qui ne sont pas converties. Ce volet est visible uniquement lorsqu’un objet avec le code est sélectionné dans le volet gauche.  
  
Cliquez sur les numéros de ligne pour définir ou supprimer des signets. Utilisez les boutons en haut du volet pour naviguer dans le code.  
  
**Volet messages**  
Affiche les erreurs, avertissements et les messages d’information qui sont générés lors de la création du rapport d’évaluation. Les messages sont regroupés par numéro. Pour afficher le code qui a provoqué l’erreur, cliquez sur **erreur**, **avertissement**, ou **Info**, développez la catégorie de messages, puis cliquez sur un message.  
  
