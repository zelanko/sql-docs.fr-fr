---
title: SQLTransact (Visual FoxPro ODBC Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTransact function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 92cf86c0-f7a8-44d7-b59f-a1342677440b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3910f24578bcbc409a84573e994c0680ed5949b2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299219"
---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Ce sujet contient des informations visuelles spécifiques à FoxPro ODBC Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soutien: Complet  
  
 Conformité API ODBC : Niveau de base  
  
 Demande une opération de validation ou de restauration pour toutes les opérations actives sur toutes les poignées de relevé *(hstmt*s) associées à une connexion ou pour toutes les connexions associées à la poignée de l’environnement, *henv*. **SQLTransact** ne fonctionne que pour les sources de données qui sont [des bases de données](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Si un commit échoue en mode manuel, la transaction reste active; vous pouvez choisir de annuler la transaction ou de réessayer l’opération de validation. Si une opération de validation échoue en mode transaction automatique, la transaction est annulée automatiquement; la transaction ne peut pas être inactive.  
  
 Pour plus d’informations, voir [SQLTransact](../../odbc/reference/syntax/sqltransact-function.md) dans la *référence du programmeur ODBC*.
