---
title: Libération des descripteurs | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305600"
---
# <a name="freeing-descriptors"></a>Libération des descripteurs
Les descripteurs alloués explicitement peuvent être libérés explicitement, en appelant **SQLFreeHandle** avec *comme HandleType* de SQL_HANDLE_DESC, ou implicitement, lorsque le handle de connexion est libéré. Lorsqu’un descripteur alloué explicitement est libéré, tous les descripteurs d’instruction auxquels le descripteur libéré a été appliqué reprennent automatiquement les descripteurs alloués implicitement.  
  
 Les descripteurs alloués implicitement peuvent être libérés uniquement en appelant **SQLDisconnect**, ce qui supprime toutes les instructions ou descripteurs ouverts sur la connexion, ou en appelant **SQLFreeHandle** avec un *comme HandleType* de SQL_HANDLE_STMT pour libérer un handle d’instruction et tous les descripteurs alloués implicitement associés à l’instruction. Un descripteur alloué implicitement ne peut pas être libéré en appelant **SQLFreeHandle** avec un *comme HandleType* de SQL_HANDLE_DESC.  
  
 Même lorsqu’elle est libérée, un descripteur alloué implicitement reste valide et **SQLGetDescField** peut être appelé sur ses champs.
