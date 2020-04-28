---
title: Limitations de chaîne | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 61f81ff3da882095a0a6c41bb5061addd497a5d2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306060"
---
# <a name="string-limitations"></a>Limitations des chaînes
La longueur maximale d’une chaîne d’instruction SQL est de 65 000 caractères.  
  
 Lorsque le pilote Microsoft Access est utilisé, seules les constantes de chaîne SQL-92 (avec des guillemets simples, et non des guillemets doubles) sont prises en charge.  
  
 Le caractère de barre verticale (&#124;) ne peut pas être utilisé dans une chaîne, que le caractère soit placé entre guillemets ou non.  
  
 Pour une interopérabilité maximale, les applications doivent passer des chaînes dans les paramètres, plutôt que de passer des chaînes entre guillemets.
