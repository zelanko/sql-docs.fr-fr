---
description: Enregistrements de descripteurs liés
title: Enregistrements de descripteurs liés | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- bound descriptor records [ODBC]
- descriptors [ODBC], bound descriptor records
ms.assetid: 55d09344-6682-40f6-b634-036b134ff650
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fcf88374967b5a9d8426d16c9e92c06e4eef32cb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476801"
---
# <a name="bound-descriptor-records"></a>Enregistrements de descripteurs liés
Lorsque l’application définit le champ SQL_DESC_DATA_PTR d’un enregistrement de descripteur afin qu’elle ne contienne plus de valeur null, l’enregistrement est considéré comme étant *lié*.  
  
 Si le descripteur est un APD, chaque enregistrement lié constitue un paramètre lié. Pour les paramètres d’entrée, l’application doit lier un paramètre pour chaque marqueur de paramètre dynamique dans l’instruction SQL avant d’exécuter l’instruction. Pour les paramètres de sortie, l’application n’a pas besoin de lier le paramètre.  
  
 Si le descripteur est un ARD, qui décrit une ligne de données de base de données, chaque enregistrement lié constitue une colonne liée.
