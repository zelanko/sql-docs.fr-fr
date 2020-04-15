---
title: Libérer les descripteurs (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeHandle function [ODBC]
- descriptors [ODBC], allocating and freeing
- freeing descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 317213f4-0ebb-4bf8-a37a-4d6b1313823f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af30ceb29e032764b89aa2069086aa898a7d35db
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305600"
---
# <a name="freeing-descriptors"></a>Libération des descripteurs
Les descripteurs explicitement attribués peuvent être libérés explicitement, soit en appelant **SQLFreeHandle** avec *HandleType* de SQL_HANDLE_DESC, ou implicitement, lorsque la poignée de connexion est libérée. Lorsqu’un descripteur explicitement attribué est libéré, toutes les poignées de déclaration auxquelles le descripteur libéré appliqué retournent automatiquement aux descripteurs qui leur sont implicitement attribués.  
  
 Les descripteurs implicitement attribués ne peuvent être libérés qu’en appelant **SQLDisconnect**, qui laisse tomber toutes les déclarations ou les descripteurs ouverts sur la connexion, ou en appelant **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_STMT pour libérer une poignée de déclaration et tous les descripteurs implicitement attribués associés à la déclaration. Un descripteur implicitement attribué ne peut pas être libéré en appelant **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_DESC.  
  
 Même lorsqu’il est libéré, un descripteur implicitement attribué reste valide, et **SQLGetDescField** peut être appelé sur ses champs.
