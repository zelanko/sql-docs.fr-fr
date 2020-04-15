---
title: Champs différés (en anglais) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 094aba353e10ed568e1959b1d655109296507dee
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305970"
---
# <a name="deferred-fields"></a>Champs différés
Les valeurs des *champs différés* ne sont pas utilisées lorsqu’elles sont définies, mais le conducteur enregistre les adresses des variables pour un effet différé. Pour un descripteur de paramètre d’application, le conducteur utilise le contenu des variables au moment de l’appel à **SQLExecDirect** ou **SQLExecute**. Pour un descripteur de ligne d’application, le conducteur utilise le contenu des variables au moment de l’aller chercher.  
  
 Voici les champs différés :  
  
-   Les SQL_DESC_DATA_PTR et SQL_DESC_INDICATOR_PTR champs d’un dossier descripteur.  
  
-   Le SQL_DESC_OCTET_LENGTH_PTR champ d’un dossier descripteur d’application.  
  
-   Dans le cas d’un multirow fetch, les champs SQL_DESC_ARRAY_STATUS_PTR et SQL_DESC_ROWS_PROCESSED_PTR d’un en-tête descripteur.  
  
 Lorsqu’un descripteur est attribué, les champs différés de chaque dossier descripteur ont d’abord une valeur nulle. Le sens de la valeur nulle est le suivant :  
  
-   Si SQL_DESC_ARRAY_STATUS_PTR a une valeur nulle, un aller chercher multirow ne parvient pas à retourner ce composant de l’information diagnostique par rangée.  
  
-   Si SQL_DESC_DATA_PTR a une valeur nulle, le dossier n’est pas lié.  
  
-   Si le champ SQL_DESC_OCTET_LENGTH_PTR d’un ARD a une valeur nulle, le conducteur ne retourne pas les informations de longueur pour cette colonne.  
  
-   Si le champ SQL_DESC_OCTET_LENGTH_PTR d’une DPA a une valeur nulle et que le paramètre est une chaîne de caractères, le conducteur suppose que la chaîne est annulée. Pour les paramètres dynamiques de sortie, une valeur nulle dans ce domaine empêche le conducteur de retourner les informations de longueur. (Si le champ SQL_DESC_TYPE n’indique pas un paramètre de caractère-corde, le champ SQL_DESC_OCTET_LENGTH_PTR est ignoré.)  
  
 L’application ne doit pas traiter ou rejeter les variables utilisées pour les champs différés entre le moment où elle les associe aux champs et le moment où le conducteur les lit ou les écrit.
