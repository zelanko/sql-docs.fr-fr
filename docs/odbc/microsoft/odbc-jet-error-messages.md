---
title: Messages d’erreur d’avion d’ODBC (fr) Microsoft Docs
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
ms.openlocfilehash: e8fa6e672b69c7791e66dc3919e6fcd22b7c3de7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293109"
---
# <a name="odbc-jet-error-messages"></a>Messages d’erreur d’ODBC Jet
Pour les erreurs qui se produisent dans la source de données, le pilote ODBC renvoie un message d’erreur retourné à celui-ci par la bibliothèque de fichiers ODBC. Pour les erreurs qui se produisent dans le conducteur ODBC ou le gestionnaire de conducteur, le conducteur retourne un message d’erreur basé sur le texte associé à la SQLSTATE.  
  
 Les messages d’erreur ont le format suivant :  
  
```  
[vendor][ODBC-component][data-source]message-text  
```  
  
 Les préfixes entre parenthèses ([]) identifient l’emplacement de l’erreur. Lorsque l’erreur se produit dans le gestionnaire de *conducteur,* la source de données n’est pas donnée. Lorsque l’erreur se produit dans la source de données, les préfixes *[fournisseur]* et *[ODBC-composant*] identifient le fournisseur et le nom du composant ODBC qui a reçu l’erreur de la source de données.  
  
 Le tableau suivant montre les messages d’erreur retournés par le gestionnaire de pilote et le pilote ISAM :  
  
|Message d’erreur|Emplacement d’erreur|  
|-------------------|--------------------|  
|[Microsoft] [ODBC Driver Manager] *message-texte*|Gestionnaire de pilote (Odbc32.dll)|  
|[Microsoft] [ODBC *nom du conducteur*] *message-texte*|Pilote ISAM (voir Pilotes ISAMs)|
