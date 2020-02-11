---
title: Limitations des prédicats LIKE | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8cd3cebfcf20df2f8a3a786ea66fd28dd76307c0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68119707"
---
# <a name="like-predicate-limitations"></a>LIKE, prédicat - limitations
Si les données d’une colonne comprendront plus de 255 caractères, la comparaison LIKE sera basée uniquement sur les 255 premiers caractères.  
  
 Un LIKE utilisé dans une procédure est pris en charge uniquement avec des modèles de constantes. Les pilotes de base de données de bureau prennent en charge SQL-92 comme critères spéciaux.  
  
 L’utilisation d’une clause Escape dans un prédicat LIKE n’est pas prise en charge.  
  
 Une comparaison LIKE ne doit pas être effectuée sur une colonne contenant des données d’un type de données numérique ou float. Les résultats peuvent être imprévisibles. Pour plus d’informations, consultez le *Guide du programmeur Microsoft Jet moteur de base de données*.
