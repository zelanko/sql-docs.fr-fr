---
title: Champs différés | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], deferred fields
- deferred fields [ODBC]
ms.assetid: 5abeb9cc-4070-4f43-a80d-ad6a2004e5f3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c2c229d31941d5cef0da253545cecd7d1496ee4a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076823"
---
# <a name="deferred-fields"></a>Champs différés
Les valeurs des *champs différés* ne sont pas utilisées lorsqu’ils sont définis, mais le pilote enregistre les adresses des variables pour un effet différé. Pour un descripteur de paramètre d’application, le pilote utilise le contenu des variables au moment de l’appel à **SQLExecDirect** ou **SQLExecute**. Pour un descripteur de ligne d’application, le pilote utilise le contenu des variables au moment de l’extraction.  
  
 Les champs suivants sont différés :  
  
-   Champs SQL_DESC_DATA_PTR et SQL_DESC_INDICATOR_PTR d’un enregistrement de descripteur.  
  
-   Champ SQL_DESC_OCTET_LENGTH_PTR d’un enregistrement de descripteur d’application.  
  
-   Dans le cas d’une extraction multiligne, les champs SQL_DESC_ARRAY_STATUS_PTR et SQL_DESC_ROWS_PROCESSED_PTR d’un en-tête de descripteur.  
  
 Lorsqu’un descripteur est alloué, les champs différés de chaque enregistrement de descripteur ont initialement une valeur null. La signification de la valeur null est la suivante :  
  
-   Si SQL_DESC_ARRAY_STATUS_PTR a une valeur null, une extraction multiligne ne parvient pas à retourner ce composant des informations de diagnostic par ligne.  
  
-   Si SQL_DESC_DATA_PTR a une valeur null, l’enregistrement est indépendant.  
  
-   Si le champ SQL_DESC_OCTET_LENGTH_PTR d’un ARD a une valeur null, le pilote ne retourne pas d’informations sur la longueur de cette colonne.  
  
-   Si le champ SQL_DESC_OCTET_LENGTH_PTR d’un APD a une valeur null et que le paramètre est une chaîne de caractères, le pilote part du principe que cette chaîne se termine par un caractère null. Pour les paramètres dynamiques de sortie, une valeur null dans ce champ empêche le pilote de retourner des informations de longueur. (Si le champ SQL_DESC_TYPE n’indique pas un paramètre de chaîne de caractères, le champ SQL_DESC_OCTET_LENGTH_PTR est ignoré.)  
  
 L’application ne doit pas désallouer ou ignorer les variables utilisées pour les champs différés entre le moment où elle les associe aux champs et le moment où le pilote les lit ou les écrit.
