---
title: Rapport d’évaluation (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9e13eba0-e3cf-4205-974f-c00f982061de
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b8217aa8346afd27ceba71b4cc929597e74dee9d
ms.sourcegitcommit: b70b99c2e412b4d697021f3bf1a92046aafcbe37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2018
ms.locfileid: "40392713"
---
# <a name="assessment-report-db2tosql"></a>Rapport d’évaluation (DB2ToSQL)
La fenêtre de rapport d’évaluation affiche les résultats de la conversion d’objets de base de données à [!INCLUDE[tsql](../../includes/tsql-md.md)] syntaxe, et peut également aider à vous estimer le coût et complexité de vos projets de migration.  
  
Pour accéder au rapport d’évaluation, sélectionner les objets à convertir dans l’Explorateur de métadonnées de source, avec le bouton droit **schémas** ou **synonymes**, puis sélectionnez **créer un rapport**.  
  
## <a name="options"></a>Options  
  
|||  
|-|-|  
|Terme|Définition|  
|**Statistiques de conversion**|Affiche les statistiques de la conversion en type d’instruction. Ce volet est visible lorsqu’un objet de groupe, tel qu’un schéma, ou un objet sans code est sélectionné dans le volet gauche.|  
|**Objets par catégories**|Affiche le nombre d’objets par catégorie. Ce volet est visible uniquement lorsqu’un objet de groupe, tel qu’un schéma, ou un objet sans code est sélectionné dans le volet gauche.|  
|**Statistiques**|Affiche les statistiques de conversion de l’objet sélectionné. Ce volet est visible uniquement lorsqu’un objet avec le code est sélectionné dans le volet gauche. Vous devrez peut-être développer **statistiques**, ce qui est immédiatement au-dessus du **Source** volet, pour afficher ce volet.|  
|**Source**|Affiche le code de DB2 pour l’objet sélectionné et met en évidence de code qui n’a pas été converti à [!INCLUDE[tsql](../../includes/tsql-md.md)]. Ce volet est visible uniquement lorsqu’un objet avec le code est sélectionné dans le volet gauche.<br /><br />Cliquez sur les numéros de ligne pour définir ou supprimer des signets. Utilisez les boutons en haut du volet pour naviguer dans le code.|  
|**Cible**|Montre la conversion du résultant [!INCLUDE[tsql](../../includes/tsql-md.md)] code pour l’objet sélectionné et les messages d’erreur pour le code qui ne sont pas converties. Ce volet est visible uniquement lorsqu’un objet avec le code est sélectionné dans le volet gauche.<br /><br />Cliquez sur les numéros de ligne pour définir ou supprimer des signets. Utilisez les boutons en haut du volet pour naviguer dans le code.|  
|**Volet messages**|Affiche les erreurs, avertissements et les messages d’information qui ont été générées lors de la création du rapport d’évaluation. Les messages sont regroupés par numéro. Pour afficher le code qui a provoqué l’erreur, cliquez sur **erreurs**, **avertissements**, ou **Info**, développez la catégorie de messages, puis cliquez sur un message.|  
  
