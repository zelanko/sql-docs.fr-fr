---
title: ODBC Jet des Messages d’erreur | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 85e0f9a8bc7015a0ad5b12ce46a6c94ab31ca43c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915812"
---
# <a name="odbc-jet-error-messages"></a>Messages d’erreur d’ODBC Jet
Pour les erreurs qui se produisent dans la source de données, le pilote ODBC retourne un message d’erreur qui lui a été retourné par la bibliothèque de fichier ODBC. Pour les erreurs qui se produisent dans le pilote ODBC ou le Gestionnaire de pilotes, les retours de pilote un message d’erreur en fonction du texte associé à la variable SQLSTATE.  
  
 Messages d’erreur ont le format suivant :  
  
```  
[vendor][ODBC-component][data-source]message-text  
```  
  
 Les préfixes de crochets ([]) identifient l’emplacement de l’erreur. Lorsque l’erreur se produit dans le Gestionnaire de pilotes, *source de données* n’est pas spécifié. Lorsque l’erreur se produit dans la source de données, le [*fournisseur*] et [*ODBC-composant*] préfixes d’identifient le fournisseur et le nom du composant qui a reçu l’erreur à partir de la source de données ODBC.  
  
 Le tableau suivant présente les messages d’erreur retournés par le Gestionnaire de pilotes et le pilote ISAM :  
  
|Message d’erreur|Emplacement de l’erreur|  
|-------------------|--------------------|  
|[Microsoft] [Gestionnaire de pilotes ODBC] *texte du message*|Gestionnaire de pilotes (Odbc32.dll)|  
|[Microsoft] [ODBC *-nom du pilote*]*texte du message*|Pilote ISAM (voir les pilotes ISAM pilote)|
