---
title: SQLParamOptions (Visual FoxPro ODBC Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLParamOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 7f94a6e2-9c34-405c-b2b0-304d94269715
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dd714ce7774265a2afd00d42894d644a516bc402
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299469"
---
# <a name="sqlparamoptions-visual-foxpro-odbc-driver"></a>SQLParamOptions (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Ce sujet contient des informations visuelles spécifiques à FoxPro ODBC Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soutien: Complet  
  
 Conformité API ODBC: Niveau 1  
  
 Permet à une application de spécifier plusieurs valeurs pour l’ensemble de paramètres attribués par [SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md). La capacité de spécifier plusieurs valeurs pour un ensemble de paramètres est utile pour les encarts en vrac et d’autres travaux qui exigent que la source de données traite la même déclaration SQL plusieurs fois avec diverses valeurs de paramètres. Par exemple, une application peut spécifier trois ensembles de valeurs pour l’ensemble de paramètres associés à une instruction **INSERT,** puis exécuter l’instruction **INSERT** une fois pour effectuer les trois opérations d’insertion.  
  
 Pour plus d’informations, voir [SQLParamOptions](../../odbc/reference/syntax/sqlparamoptions-function.md) dans la *référence du programmeur ODBC*.
