---
title: "La libération de descripteurs | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLFreeHandle function [ODBC]
- descriptors [ODBC], allocating and freeing
- freeing descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 317213f4-0ebb-4bf8-a37a-4d6b1313823f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d1c70c82196907fc0bd9747a8ece089d4e4ab514
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="freeing-descriptors"></a>La libération de descripteurs
Descripteurs explicitement alloués peuvent être soit libérée explicitement, en appelant **SQLFreeHandle** avec *HandleType* de SQL_HANDLE_DESC, ou implicitement, lorsque le handle de connexion est libéré. Lorsqu’un descripteur explicitement alloué est libéré, tous les descripteurs d’instruction auquel le descripteur libéré automatiquement appliqué rétablir les descripteurs implicitement leur a été allouées.  
  
 Descripteurs implicitement alloués peuvent être libérées uniquement en appelant **SQLDisconnect**, qui supprime toutes les instructions ou descripteurs sur la connexion ou en appelant **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_STMT pour libérer un descripteur d’instruction et les descripteurs implicitement alloués est associés à l’instruction. Un descripteur implicitement alloué ne peut pas être libéré en appelant **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_DESC.  
  
 Même lorsque libéré, un descripteur implicitement alloué reste valide, et **SQLGetDescField** peut être appelée sur ses champs.
