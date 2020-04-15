---
title: Dossiers diagnostiques (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- handles [ODBC], diagnostic records
- header records [ODBC]
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 92c73f9b-3ed7-410d-9cec-2771004aae60
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b564f2837bc76e04011170e191d00c08d10c119d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305180"
---
# <a name="diagnostic-records"></a>Enregistrements de diagnostic
Associés à chaque environnement, connexion, déclaration, et poignée descripteur sont *des dossiers diagnostiques*. Ces dossiers contiennent des informations diagnostiques sur la dernière fonction appelée qui utilisait une poignée particulière. Les enregistrements ne sont remplacés que lorsqu’une autre fonction est appelée à l’aide de cette poignée. Il n’y a pas de limite au nombre de dossiers diagnostiques qui peuvent être stockés à tout moment.  
  
 Il existe deux types de dossiers diagnostiques : un *enregistrement d’en-tête* et des enregistrements de *statut*nuls ou plus. Le record d’en-tête est record 0; les registres d’état sont des enregistrements 1 et plus. Les dossiers diagnostiques sont composés d’un certain nombre de champs distincts, qui sont différents pour l’enregistrement d’en-tête et les enregistrements d’état. En outre, les composants ODBC peuvent définir leurs propres champs de dossiers diagnostiques.  
  
 Bien que les dossiers diagnostiques puissent être considérés comme des structures, il n’est pas nécessaire qu’elles soient réellement des structures; comment un conducteur stocke l’information diagnostique est spécifique au conducteur.  
  
 Les champs dans les dossiers diagnostiques sont récupérés avec **SQLGetDiagField**. Le SQLSTATE, le numéro d’erreur natif et les champs de messages diagnostiques des dossiers d’état peuvent être récupérés en un seul appel avec **SQLGetDiagRec**.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Enregistrement d’en-tête](../../../odbc/reference/develop-app/header-record.md)  
  
-   [Enregistrements d’état](../../../odbc/reference/develop-app/status-records.md)
