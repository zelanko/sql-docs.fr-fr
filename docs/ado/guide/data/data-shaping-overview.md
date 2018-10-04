---
title: Vue d’ensemble de la mise en forme des données | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data shaping [ADO], overview
ms.assetid: 4cb5fd29-4e56-46ac-ae48-a6771c321c0c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 64b54acb2334aa09c5d4c2fde421f1dca9f8f3c5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47761467"
---
# <a name="data-shaping-overview"></a>Vue d’ensemble de la mise en forme des données
*Mise en forme des données* revient à développer des relations hiérarchiques entre deux ou plusieurs entités logiques dans une requête. La hiérarchie peut être observée dans les relations parent-enfant entre un enregistrement d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)et un ou plusieurs enregistrements (également appelé un chapitre) d’un autre **Recordset**. Dans une relation parent-enfant, le parent **Recordset** contient l’enfant **Recordset**. Un exemple d’une telle relation hiérarchique est customers et orders. Pour chaque client dans une base de données, il peut y avoir zéro ou plusieurs commandes. La relation hiérarchique peut être récursives, ce qui signifie que les enregistrements de petit-enfant peuvent être imbriquées dans un enregistrement enfant. En principe, un enregistrement hiérarchique peut être imbriqué à n’importe quelle profondeur. Dans la pratique, ADO limite la récursivité à un maximum de 512 **Recordset**s.  
  
 Dans les colonnes générales, d’une forme **Recordset** peut contenir des données à partir d’un fournisseur de données telles que Microsoft® SQL Server, les références à un autre **Recordset**, des valeurs dérivées d’un calcul sur une seule ligne d’un  **Jeu d’enregistrements**, ou des valeurs dérivées d’une opération sur une colonne de l’intégralité d’un **Recordset**. Une colonne peut également être nouvellement créé et vide.  
  
 Lorsque vous récupérez la valeur d’une colonne qui contient une référence à un autre **Recordset**, ADO retourne automatiquement réel **Recordset** représenté par la référence. La référence à un **Recordset** est en fait une référence à un sous-ensemble de l’enfant, appelé un *chapitre*. Un seul parent peut référencer plusieurs enfants **Recordset**.  
  
 Prise en charge ADO pour la mise en forme des données vous permet d’interroger une source de données et retourner un **Recordset** dans laquelle un enregistrement (parent) représente un élément (enfant) **Recordset**. Dans le scénario de commande client, vous pouvez utiliser pour récupérer les informations des clients, ainsi que les commandes passées par chaque client dans une seule requête de mise en forme des données. La résultante **Recordset** a également connu sous la forme **Recordset**.  
  
 En outre, données de mise en forme dans ADO vous permet de créer de nouveaux **Recordset** objets sans source de données sous-jacente à l’aide de la **NEW** mot clé pour décrire les champs de parent et enfant  **Jeux d’enregistrements**. La nouvelle **Recordset** objet peut ensuite être rempli avec les données et stocké de manière permanente. Les développeurs peuvent également effectuer des calculs ou des agrégations différentes (par exemple, **somme**, **AVG**, et **MAX**) sur les champs enfants. Mise en forme des données peut également créer un parent **Recordset** à partir d’un enfant **Recordset** en regroupant des enregistrements de l’enfant et en plaçant une ligne dans le parent pour chaque groupe dans l’enfant.  
  
 SQL régulière permet de vous permettent de récupérer des données à l’aide **joindre** syntaxe, mais cela peut être inefficace et difficile à gérer, car les données redondantes parent sont répétées dans chaque enregistrement renvoyé pour une relation parent-enfant donnée. Mise en forme des données peut associer un enregistrement de parent unique dans le parent **Recordset** à plusieurs enregistrements enfants de l’enfant **Recordset**, en évitant la redondance d’un **joindre**. La plupart des gens rechercher le parent-enfant plusieurs **Recordset** modèle de programmation plus naturel et plus facile à utiliser que le seul **Recordset joindre** modèle.
