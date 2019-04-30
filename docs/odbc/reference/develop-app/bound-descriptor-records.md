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
manager: craigg
ms.openlocfilehash: 6f7d21a1166868603f9389ab4ef5c5b3448b0312
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199527"
---
# <a name="bound-descriptor-records"></a>Enregistrements de descripteurs liés
Lorsque l’application définit le champ SQL_DESC_DATA_PTR d’un enregistrement de descripteur pour qu’il contienne n’est plus une valeur null, l’enregistrement est dite *lié*.  
  
 Si le descripteur est un APD, chaque enregistrement lié constitue un paramètre lié. Pour les paramètres d’entrée, l’application doit lier un paramètre pour chaque marqueur de paramètre dynamique dans l’instruction SQL avant d’exécuter l’instruction. Pour les paramètres de sortie, l’application ne doive pas lier le paramètre.  
  
 Si le descripteur est un ARD, qui décrit une ligne de base de données, chaque enregistrement lié constitue une colonne dépendante.
