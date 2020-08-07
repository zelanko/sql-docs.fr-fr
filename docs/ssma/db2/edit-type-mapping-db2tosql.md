---
title: Modifier le mappage de type (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f93c4b7d-74fc-4856-bf42-035289918e83
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 5dc6cd8939dbc7d5d42417b06c938c9ae8d3f7e8
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87937188"
---
# <a name="edit-type-mapping-db2tosql"></a>Modifier le mappage de type (DB2ToSQL)
La boîte de dialogue **modifier le mappage de type** vous permet de spécifier la manière dont les types sont mappés entre les objets de base de données source et de destination.  
  
Vous pouvez accéder à cette boîte de dialogue à plusieurs endroits :  
  
-   Lorsque vous sélectionnez une base de données source ou un objet de base de données, l’onglet **mappage de type** s’affiche à droite de l’Explorateur de métadonnées. Cliquez sur **Ajouter** pour ajouter un nouveau mappage de type, ou cliquez sur **modifier** pour modifier un mappage de type existant.  
  
-   Dans le menu **Outils** , sélectionnez **paramètres du projet** ou paramètres du **projet par défaut**. Dans la boîte de dialogue qui en résulte, sélectionnez **mappage de type**. Cliquez sur **Ajouter** pour ajouter un nouveau mappage de type, ou cliquez sur **modifier** pour modifier un mappage de type existant.  
  
Les mappages de types spécifiques aux tables remplacent les mappages de type de projet et de base de données. Les mappages spécifiques à la base de données remplacent les mappages de projet.  
  
## <a name="options"></a>Options  
**Type de source**  
Sélectionnez le type de données source à mapper à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.  
  
Si le type de données est de longueur variable, les champs suivants s’affichent sous le **type de source**:  
  
**From**  
Spécifiez la longueur minimale pour ce mappage. Par exemple, pour le type de données **nchar** , vous pouvez entrer 10 pour spécifier que ce mappage s’adresse à une plage commençant par **nchar (10)**.  
  
**To**  
Spécifiez la longueur maximale pour ce mappage. Par exemple, pour le type de données **nchar** , vous pouvez entrer 20 pour spécifier que ce mappage est destiné à une plage se terminant par **nchar (20)**.  
  
**Type de cible**  
Sélectionnez le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données auquel le type de données source est mappé. Lorsque SSMA crée la table ou la procédure stockée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le type de données source passe à ce type de données.  
  
Si le type de données est de longueur variable, le champ suivant s’affiche sous **type de cible**:  
  
**Remplacer par**  
Spécifiez la longueur cible pour ce mappage. Par exemple, pour le type de données **nvarchar** , vous pouvez entrer 20 pour spécifier que le type de données source spécifié doit être mappé à **nvarchar (20)**.  
  
