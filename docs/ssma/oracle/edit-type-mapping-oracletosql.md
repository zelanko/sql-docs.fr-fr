---
title: Modifier le mappage de Type (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 7078b4ed-c779-4bf3-8db8-f9dcb3edd50f
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: ee8d2e4c16987f5cc012f734cdf649cde7f4ebb8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63288583"
---
# <a name="edit-type-mapping-oracletosql"></a>Modifier le mappage de type (OracleToSQL)
Le **modifier le mappage de Type** boîte de dialogue vous permet de spécifier comment les types sont mappés entre les objets de base de données source et de destination.  
  
Vous pouvez accéder à cette boîte de dialogue à plusieurs endroits :  
  
-   Lorsque vous sélectionnez une base de données source ou un objet de base de données, le **le mappage de Type** onglet s’affiche à droite de l’Explorateur de métadonnées. Cliquez sur **ajouter** pour ajouter un nouveau mappage de type, ou cliquez sur **modifier** pour modifier un mappage de type existant.  
  
-   Sur le **outils** menu, sélectionnez **paramètres du projet** ou **par défaut des paramètres de projet**. Dans la boîte de dialogue, sélectionnez **le mappage de Type**. Cliquez sur **ajouter** pour ajouter un nouveau mappage de type, ou cliquez sur **modifier** pour modifier un mappage de type existant.  
  
Mappages de types de table spécifiques de remplacent la base de données et les mappages de type de projet. Mappages spécifiques à la base de données remplacent les mappages de projet.  
  
## <a name="options"></a>Options  
**Type de source**  
Sélectionnez le type de données source à mapper à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.  
  
Si le type de données est de longueur variable, les champs suivants seront affiche sous **type de Source**:  
  
**From**  
Spécifiez la longueur minimale pour ce mappage. Par exemple, pour le **nchar** type de données, vous pouvez entrer 10 pour spécifier que ce mappage est pour une plage commençant à **nchar(10)**.  
  
**Pour**  
Spécifiez la longueur maximale pour ce mappage. Par exemple, pour le **nchar** type de données, vous pouvez entrer 20 pour spécifier que ce mappage s’applique à une plage et se termine au **nchar (20)**.  
  
**Type de cible**  
Sélectionnez le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données à laquelle le type de données source est mappé. Lorsque SSMA crée la table ou la procédure stockée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le type de source de données changera à ce type de données.  
  
Si le type de données est de longueur variable, le champ suivant apparaît sous **type cible**:  
  
**Replace with**  
Spécifier la longueur de la cible pour ce mappage. Par exemple, pour le **nvarchar** type de données, vous pouvez entrer 20 pour spécifier que le type de données source spécifiée doit être mappé à **nvarchar (20)**.  
  
