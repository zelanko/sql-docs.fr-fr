---
title: SET EXCLUSIVE, commande | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET EXCLUSIVE command [ODBC]
ms.assetid: d4fe12c5-7e8b-4d20-9ea4-2bcaffb271f2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9d1a37043d332b54d0d5c5ebb7b2ba9f3acce000
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071757"
---
# <a name="set-exclusive-command"></a>SET EXCLUSIVE, commande
Spécifie si les fichiers de la table sont ouverts pour une utilisation exclusive ou partagée sur un réseau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET EXCLUSIVE ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ON  
 Limite d’accessibilité d’une table ouverte sur un réseau à l’utilisateur qui l’avez ouverte. La table n’est pas accessible à d’autres utilisateurs sur le réseau. SET de ON exclusif empêche également tous les autres utilisateurs ayant un accès en lecture seule.  
  
 OFF  
 (Valeur par défaut pour le pilote ; les valeurs par défaut pour Visual FoxPro sont ON pour la session de données globales et désactivée (OFF) pour une session de données privées). Permet à une table est ouverte sur un réseau partagé et modifiés par n’importe quel utilisateur sur le réseau.  
  
## <a name="remarks"></a>Notes  
 Modification du paramètre de valeur exclusif ne change pas l’état des tables précédemment ouverts. Par exemple, si une table est ouvert avec définir exclusif la valeur ON et définissez exclusif est modifié ultérieurement à OFF, la table conserve son état de l’usage exclusif.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration d’ODBC pour Visual FoxPro, boîte de dialogue](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
