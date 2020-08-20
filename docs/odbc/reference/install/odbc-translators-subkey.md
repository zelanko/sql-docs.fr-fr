---
description: Sous-clé de convertisseurs ODBC
title: Sous-clé ODBC Translators | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translator subkey [ODBC]
- subkeys [ODBC], translator subkey
- registry entries for components [ODBC], translator subkey
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 46308518f1f806cea21bbb824312d5269f8b61e4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499712"
---
# <a name="odbc-translators-subkey"></a>Sous-clé de convertisseurs ODBC
Les valeurs de la sous-clé ODBC Translators listent les convertisseurs installés. Le format de ces valeurs est indiqué dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|*Traducteur-DESC*|REG_SZ|**Installé**|  
  
 Le nom *Translator-DESC* est défini par le développeur du traducteur.  
  
 Supposons, par exemple, qu’un utilisateur ait installé le convertisseur de page de codes Microsoft® et un traducteur ASCII en codage EBCDIC personnalisé. Les valeurs de la sous-clé ODBC Translators peuvent être les suivantes :  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
