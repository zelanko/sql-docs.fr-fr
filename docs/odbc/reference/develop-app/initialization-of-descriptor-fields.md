---
title: Initialisation de Descriptor Fields (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- initializing descriptor fields [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1da157cb-8ea9-4a56-983b-1c45650217c5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e4ed6479a60f1d0695107c216b2f0c94a55f68ff
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300119"
---
# <a name="initialization-of-descriptor-fields"></a>Initialisation de champs de descripteur
Lorsqu’un descripteur de ligne d’application est attribué, ses champs reçoivent des valeurs initiales telles qu’indiquées dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). La valeur initiale du champ SQL_DESC_TYPE est SQL_DEFAULT. Cela prévoit un traitement standard des données de base de données pour la présentation à l’application. L’application peut spécifier le traitement différent des données en fixant les champs de l’enregistrement descripteur.  
  
 La valeur initiale de SQL_DESC_ARRAY_SIZE dans l’en-tête descripteur est de 1. L’application peut modifier ce champ pour permettre à multirow aller chercher.  
  
 Le concept de valeur par défaut n’est pas valable pour les champs d’un IRD. Une application ne peut accéder aux champs d’un IRD que lorsqu’il y a une déclaration préparée ou exécutée qui lui est associée.  
  
 Certains champs d’une DPI ne sont définis qu’après que l’IPD a été automatiquement peuplé par le conducteur. Si ce n’est pas le cas, ils ne sont pas définis. Ces champs sont SQL_DESC_CASE_SENSITIVE, SQL_DESC_FIXED_PREC_SCALE, SQL_DESC_TYPE_NAME, SQL_DESC_UNSIGNED et SQL_DESC_LOCAL_TYPE_NAME.
