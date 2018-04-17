---
title: Messages d’erreur à Jet ODBC | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error messages (ODBC driver for oracle)
ms.assetid: f8d2a8f2-0316-42c4-bc34-5367661634ae
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b62b26425c1e9126ea5d6ad5a3a4c3d944a5b79a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="odbc-jet-error-messages"></a>Messages d’erreur à Jet ODBC
Pour les erreurs qui se produisent dans la source de données, le pilote ODBC retourne un message d’erreur qui lui a été retourné par la bibliothèque de fichier ODBC. Pour les erreurs qui se produisent dans le pilote ODBC ou le Gestionnaire de pilotes, les retours de pilote un message d’erreur en fonction du texte associé à la valeur SQLSTATE.  
  
 Messages d’erreur ont le format suivant :  
  
```  
[vendor][ODBC-component][data-source]message-text  
```  
  
 Les préfixes de crochets ([]) identifient l’emplacement de l’erreur. Lorsque l’erreur se produit dans le Gestionnaire de pilotes, *source de données* n’est pas spécifié. Lorsque l’erreur se produit dans la source de données, le [*fournisseur*] et [*composants ODBC*] préfixes d’identifient le fournisseur et le nom du composant qui a reçu l’erreur à partir de la source de données ODBC.  
  
 Le tableau suivant présente les messages d’erreur retournés par le Gestionnaire de pilotes et le pilote ISAM :  
  
|Message d'erreur|Emplacement de l’erreur|  
|-------------------|--------------------|  
|[Microsoft] [Gestionnaire de pilotes ODBC] *texte du message*|Gestionnaire de pilotes (Odbc32.dll)|  
|[Microsoft] [ODBC *-nom du pilote*]*texte du message*|Pilote ISAM (voir pilotes ISAM du pilote)|
