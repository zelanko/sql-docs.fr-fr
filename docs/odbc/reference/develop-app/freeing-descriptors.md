---
title: Libération de descripteurs | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d643ccad0110796127524a10e82aef7c3339b163
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63061487"
---
# <a name="freeing-descriptors"></a>Libération des descripteurs
Descripteurs alloués explicitement peuvent être soit libérée explicitement, en appelant **SQLFreeHandle** avec *HandleType* de SQL_HANDLE_DESC, ou implicitement, lorsque la connexion est libéré. Quand un descripteur explicitement alloué est libéré, tous les descripteurs d’instruction à laquelle le descripteur libéré appliqué automatiquement rétablir les descripteurs alloués implicitement pour eux.  
  
 Descripteurs alloués implicitement peuvent être libérées uniquement en appelant **SQLDisconnect**, qui supprime toutes les instructions ou descripteurs sur la connexion ou en appelant **SQLFreeHandle** avec un  *HandleType* de SQL_HANDLE_STMT pour libérer un descripteur d’instruction et les descripteurs alloués implicitement est associés à l’instruction. Un descripteur alloué implicitement ne peut pas être libéré en appelant **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_DESC.  
  
 Même lorsque libéré, un descripteur alloué implicitement reste valide, et **SQLGetDescField** peut être appelée sur ses champs.
