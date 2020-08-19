---
description: SQLPrimaryKeys (pilote ODBC Visual FoxPro)
title: SQLPrimaryKeys (pilote ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLPrimaryKeys function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8dbe2903-efdc-45e0-a079-9e357c5fd81b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96b333e10c7000a8a44e957e33d0c84a3b004f43
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483342"
---
# <a name="sqlprimarykeys-visual-foxpro-odbc-driver"></a>SQLPrimaryKeys (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité de l’API ODBC : niveau 2  
  
 Retourne les noms de colonnes qui composent la clé primaire d’une table. L’implémentation du pilote ODBC Visual FoxPro de **SQLPrimaryKeys** se comporte comme suit :  
  
-   Ignore les arguments *szTableOwner* et *cbTableOwner* .  
  
-   Fonctionne uniquement pour les sources de données qui sont des [bases de](../../odbc/microsoft/visual-foxpro-terminology.md)données. Le pilote retourne l’erreur « le pilote ne prend pas en charge cette fonction » si la source de données est un répertoire de [tables libres](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Pour plus d’informations, consultez [SQLPrimaryKeys](../../odbc/reference/syntax/sqlprimarykeys-function.md) dans le *Guide de référence du programmeur ODBC*.
