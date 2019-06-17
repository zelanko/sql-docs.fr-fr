---
title: Différée champs | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 1c7800e7da867b4eb0c34fa3feeba5edb2d41cd6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63049871"
---
# <a name="deferred-fields"></a>Champs différés
Les valeurs de *différée champs* ne sont pas utilisés quand elles sont définies, mais le pilote enregistre les adresses des variables pour un effet différé. Pour un descripteur de paramètre d’application, le pilote utilise le contenu des variables au moment de l’appel à **SQLExecDirect** ou **SQLExecute**. Pour un descripteur de ligne d’application, le pilote utilise le contenu des variables au moment de l’extraction.  
  
 Champs différés sont les suivantes :  
  
-   Champs d’un enregistrement de descripteur SQL_DESC_DATA_PTR et SQL_DESC_INDICATOR_PTR.  
  
-   Le champ SQL_DESC_OCTET_LENGTH_PTR d’un enregistrement de descripteur d’application.  
  
-   Dans le cas d’une extraction multiligne, les champs SQL_DESC_ARRAY_STATUS_PTR et SQL_DESC_ROWS_PROCESSED_PTR d’un en-tête de descripteur.  
  
 Lorsqu’un descripteur est alloué, les champs de chaque enregistrement de descripteur différés ont initialement une valeur null. La signification de la valeur null est la suivante :  
  
-   Si SQL_DESC_ARRAY_STATUS_PTR a la valeur null, une extraction multiligne ne parvient pas à retourner ce composant des informations de diagnostic par ligne.  
  
-   Si SQL_DESC_DATA_PTR a la valeur null, l’enregistrement est indépendant.  
  
-   Si le champ SQL_DESC_OCTET_LENGTH_PTR d’un ARD a une valeur null, le pilote ne retourne pas d’informations sur la longueur de cette colonne.  
  
-   Si le champ SQL_DESC_OCTET_LENGTH_PTR d’un APD a une valeur null et que le paramètre est une chaîne de caractères, le pilote part du principe que la chaîne est nul. Paramètres de sortie dynamique, une valeur null dans ce champ empêche le pilote de retourner des informations de longueur. (Si le champ SQL_DESC_TYPE n’indique pas un paramètre de chaîne de caractères, le champ SQL_DESC_OCTET_LENGTH_PTR est ignoré.)  
  
 L’application ne doit pas libérer ou ignorer les variables utilisées pour les champs différés entre l’heure que les associe avec les champs et l’heure, le pilote lit ou écrit les.
