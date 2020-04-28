---
title: SQLTransact (pilote ODBC Visual FoxPro) | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299219"
---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité de l’API ODBC : niveau principal  
  
 Demande une opération de validation ou de restauration pour toutes les opérations actives sur tous les descripteurs d’instruction (*HSTMT*s) associés à une connexion ou pour toutes les connexions associées au handle d’environnement, *henv*. **SQLTransact** fonctionne uniquement pour les sources de données qui sont des [bases de](../../odbc/microsoft/visual-foxpro-terminology.md)données.  
  
 Si une validation échoue en mode manuel, la transaction reste active ; vous pouvez choisir de restaurer la transaction ou de réessayer l’opération de validation. Si une opération de validation échoue en mode de transaction automatique, la transaction est restaurée automatiquement ; la transaction ne peut pas être inactive.  
  
 Pour plus d’informations, consultez [SQLTransact](../../odbc/reference/syntax/sqltransact-function.md) dans le *Guide de référence du programmeur ODBC*.
