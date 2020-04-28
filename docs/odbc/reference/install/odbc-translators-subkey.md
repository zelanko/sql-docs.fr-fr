---
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
ms.openlocfilehash: 617416adfcddfbf041c48acbf83cb9589e34ae27
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296219"
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
