---
title: DÉFINIR la commande UNIQUE | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 29598ed97cba8be04a0c08727cffc40e663becba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063616"
---
# <a name="set-unique-command"></a>SET UNIQUE, commande
Spécifie si les enregistrements avec des valeurs de clé d’index dupliquées sont conservés dans un fichier d’index.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ACTIVÉ  
 Spécifie que tout enregistrement avec une valeur de clé d’index dupliquée ne doit pas être inclus dans le fichier d’index. Seul le premier enregistrement avec la valeur de clé d’index d’origine est inclus dans le fichier d’index.  
  
 OFF  
 (Par défaut.) Spécifie que les enregistrements avec des valeurs de clé d’index dupliquées doivent être inclus dans le fichier d’index.  
  
## <a name="remarks"></a>Notes  
 Un fichier d’index conserve son paramètre SET UNIQUE lorsque vous émettez la réindexation. Pour plus d’informations, consultez [index](../../odbc/microsoft/index-command.md).
