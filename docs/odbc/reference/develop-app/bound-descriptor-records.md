---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4d0016a2849feb5656cb3cd6dd46eff444f37058
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68118759"
---
# <a name="bound-descriptor-records"></a>Enregistrements de descripteurs liés
Lorsque l’application définit le champ SQL_DESC_DATA_PTR d’un enregistrement de descripteur afin qu’elle ne contienne plus de valeur null, l’enregistrement est considéré comme étant *lié*.  
  
 Si le descripteur est un APD, chaque enregistrement lié constitue un paramètre lié. Pour les paramètres d’entrée, l’application doit lier un paramètre pour chaque marqueur de paramètre dynamique dans l’instruction SQL avant d’exécuter l’instruction. Pour les paramètres de sortie, l’application n’a pas besoin de lier le paramètre.  
  
 Si le descripteur est un ARD, qui décrit une ligne de données de base de données, chaque enregistrement lié constitue une colonne liée.
