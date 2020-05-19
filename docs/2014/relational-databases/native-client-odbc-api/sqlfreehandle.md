---
title: SQLFreeHandle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeHandle function
ms.assetid: d374e5c8-ed35-43bf-8dd6-c37e38d9b5f1
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9345a02d446d8a4b7b82e9652444a08f68641f87
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706070"
---
# <a name="sqlfreehandle"></a>SQLFreeHandle
  En mode de validation manuelle, l'appel de **SQLFreeHandle** sur un descripteur d'instruction avec une transaction ouverte provoque une restauration des modifications en attente de la base de données. L'appel de **SQLFreeHandle** sur un descripteur d'instruction ferme toujours tous les curseurs ouverts et ignore les résultats en attente, libérant toutes les ressources associées au descripteur d'instruction.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLFreeHandle, fonction](https://go.microsoft.com/fwlink/?LinkId=59345)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
