---
title: Set UNIQUE Commande (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET UNIQUE command [ODBC]
ms.assetid: 1f69e31e-4599-47cc-ac89-b86fba8703c5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7d3d37509450d1305891100b37bfd1ad026166e8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300839"
---
# <a name="set-unique-command"></a>SET UNIQUE, commande
Précise si les enregistrements avec des valeurs clés de l’index en double sont maintenus dans un fichier indiciel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ACTIVÉ  
 Précise que tout enregistrement avec une valeur clé d’index en double ne soit pas inclus dans le fichier indiciel. Seul le premier enregistrement avec la valeur clé de l’indice d’origine est inclus dans le fichier indiciel.  
  
 OFF  
 (Par défaut.) Spécifie que les enregistrements avec des valeurs clés de l’index en double soient inclus dans le fichier indiciel.  
  
## <a name="remarks"></a>Notes  
 Un fichier indiciel conserve son paramètre SET UNIQUE lorsque vous émetssez REINDEX. Pour plus d’informations, voir [INDEX](../../odbc/microsoft/index-command.md).
