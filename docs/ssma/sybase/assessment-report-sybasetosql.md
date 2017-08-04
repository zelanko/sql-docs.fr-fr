---
title: "Rapport d’évaluation (SybaseToSQL) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: af24f2c4-5e86-4135-a4f3-a24faaeeefe7
caps.latest.revision: 4
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 1a7de1095387d52d2d7675f1d8b04cc739121636
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="assessment-report-sybasetosql"></a>Rapport d’évaluation (SybaseToSQL)
La fenêtre de rapport d’évaluation affiche les résultats de la conversion d’objets de base de données à [!INCLUDE[tsql](../../includes/tsql_md.md)] syntaxe, et vous estimez la complexité et le coût de vos projets de migration.  
  
Pour accéder au rapport d’évaluation, sélectionner les objets à convertir dans l’Explorateur de métadonnées source, avec le bouton droit **bases de données**, puis sélectionnez **créer un rapport**.  
  
## <a name="options"></a>Options  
**Statistiques de conversion**  
Affiche les statistiques de la conversion en type d’instruction. Ce volet est visible uniquement lorsqu’un objet de groupe, tel qu’un schéma, ou un objet sans code est sélectionné dans le volet gauche.  
  
**Objets par catégorie**  
Affiche les statistiques de la conversion en type d’objet. Ce volet est visible uniquement lorsqu’un objet de groupe, tel qu’un schéma, ou un objet sans code est sélectionné dans le volet gauche.  
  
**Statistiques**  
Affiche les statistiques de conversion de l’objet sélectionné. Ce volet est visible uniquement quand un objet avec le code est sélectionné dans le volet gauche. Vous devrez peut-être développer **statistiques** pour afficher ce volet.  
  
**Navigation vers la source**  
Affiche le code ASE pour l’objet sélectionné et met en surbrillance le code qui n’a pas été converti à [!INCLUDE[tsql](../../includes/tsql_md.md)]. Ce volet est visible uniquement quand un objet avec le code est sélectionné dans le volet gauche.  
  
Cliquez sur les numéros de ligne pour définir ou supprimer des signets. Utilisez les boutons en haut du volet pour parcourir le code.  
  
**Navigation de la cible**  
Montre qui en résulte de la conversion [!INCLUDE[tsql](../../includes/tsql_md.md)] code de l’objet sélectionné et les messages d’erreur pour le code qui ne sont pas converties. Ce volet est visible uniquement quand un objet avec le code est sélectionné dans le volet gauche.  
  
Cliquez sur les numéros de ligne pour définir ou supprimer des signets. Utilisez les boutons en haut du volet pour parcourir le code.  
  
**Volet messages**  
Affiche les erreurs, avertissements et messages d’information générés lors de la création du rapport d’évaluation. Les messages sont regroupés par numéro. Pour afficher le code qui a provoqué l’erreur, cliquez sur **erreur**, **avertissement**, ou **Info**, développez la catégorie de messages, puis cliquez sur un message.  
  

