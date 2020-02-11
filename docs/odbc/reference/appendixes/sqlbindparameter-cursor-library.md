---
title: SQLBindParameter (bibliothèque de curseurs) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindParameter function [ODBC], Cursor Library
ms.assetid: 04c53e4c-cd1d-40b2-9997-684ebe43499f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7943987d52554e0f5cd7723e8c9ae8a0e3afddd2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093029"
---
# <a name="sqlbindparameter-cursor-library"></a>SQLBindParameter (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande l’utilisation de la fonctionnalité de curseur du pilote.  
  
 Cette rubrique traite de l’utilisation de la fonction **SQLBindParameter** dans la bibliothèque de curseurs. Pour obtenir des informations générales sur **SQLBindParameter**, consultez [fonction SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 Une application peut appeler **SQLBindParameter** pour relier des paramètres, à condition que le type de données C, la taille de colonne et les chiffres décimaux de la colonne liée restent les mêmes.  
  
 La bibliothèque de curseurs prend en charge la définition de l’attribut d’instruction SQL_ATTR_ROW_BIND_OFFSET_PTR pour utiliser des décalages de liaison. (**SQLBindParameter** n’a pas besoin d’être appelé pour que cette reliaison se produise.)  
  
 La bibliothèque de curseurs prend en charge la liaison des paramètres de données en cours d’exécution.
