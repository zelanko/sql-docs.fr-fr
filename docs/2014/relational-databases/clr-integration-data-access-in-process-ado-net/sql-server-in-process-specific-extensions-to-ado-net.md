---
title: SQL Server des extensions spécifiques in-process à ADO.NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
author: rothja
ms.author: jroth
ms.openlocfilehash: 37d8aedc1d8f93739c2e9386665adfc67b43e312
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970787"
---
# <a name="sql-server-in-process-specific-extensions-to-adonet"></a>Extensions spécifiques in-process de SQL Server à ADO.NET
  Quatre extensions fonctionnelles principales à ADO.NET sont spécifiquement destinées à une utilisation in-process. Les rubriques suivantes traitent ces extensions en détail.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Objet SqlContext](sqlcontext-object.md)  
 Cette classe fournit l'accès aux autres extensions en faisant abstraction du contexte d'un appelant d'une routine SQL Server qui exécute le code managé in-process.  
  
 [Objet SqlPipe](sqlpipe-object.md)  
 Cette classe contient les routines pour envoyer les messages et les résultats tabulaires au client.  
  
 [Objet SqlTriggerContext](sqltriggercontext-object.md)  
 Cette classe fournit des informations sur le contexte dans lequel un déclencheur est exécuté.  
  
 [Objet SqlDataRecord](sqldatarecord-object.md)  
 La classe SqlDataRecord représente une ligne unique de données, avec ses métadonnées connexes, et permet que les procédures stockées retournent des jeux de résultats personnalisés au client.  
  
  
