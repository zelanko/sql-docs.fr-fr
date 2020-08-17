---
description: Messages d’erreur d’ODBC Jet
title: Messages d’erreur ODBC Jet | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error messages (ODBC driver for oracle)
ms.assetid: f8d2a8f2-0316-42c4-bc34-5367661634ae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19f7d4b00c9e6b206ecd563083c0fcf16ced55e3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340715"
---
# <a name="odbc-jet-error-messages"></a>Messages d’erreur d’ODBC Jet
Pour les erreurs qui se produisent dans la source de données, le pilote ODBC retourne un message d’erreur retourné par la bibliothèque de fichiers ODBC. Pour les erreurs qui se produisent dans le pilote ODBC ou le gestionnaire de pilotes, le pilote retourne un message d’erreur en fonction du texte associé à SQLSTATE.  
  
 Les messages d’erreur ont le format suivant :  
  
```  
[vendor][ODBC-component][data-source]message-text  
```  
  
 Les préfixes entre crochets ([]) identifient l’emplacement de l’erreur. Lorsque l’erreur se produit dans le gestionnaire de pilotes, la *source de données* n’est pas donnée. Lorsque l’erreur se produit dans la source de données, les préfixes [*Vendor*] et [*ODBC-Component*] identifient le fournisseur et le nom du composant ODBC qui a reçu l’erreur de la source de données.  
  
 Le tableau suivant répertorie les messages d’erreur retournés par le gestionnaire de pilotes et le pilote ISAM :  
  
|Message d'erreur|Emplacement de l’erreur|  
|-------------------|--------------------|  
|Librairie [ODBC Driver Manager] *texte du message*|Gestionnaire de pilotes (Odbc32.dll)|  
|Librairie [ODBC *Driver-Name*] *texte du message*|Pilote ISAM (voir le pilote ISAMs)|
