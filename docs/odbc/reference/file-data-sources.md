---
title: Sources de données de fichier | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], file
- file data sources [ODBC]
ms.assetid: db245c80-981a-4638-bd03-69d04bc67af0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0661aa424a7a118b8b12f4bf8433987ff83bd788
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306650"
---
# <a name="file-data-sources"></a>Sources de données de fichier
Les *sources de données de fichier* sont stockées dans un fichier et permettent aux informations de connexion d’être utilisées à plusieurs reprises par un seul utilisateur ou partagées entre plusieurs utilisateurs. Quand une source de données de fichier est utilisée, le gestionnaire de pilotes établit la connexion à la source de données à l’aide des informations contenues dans un fichier. DSN. Ce fichier peut être manipulé comme n’importe quel autre fichier. Une source de données de fichier n’a pas de nom de source de données, comme la source de données d’une machine, et n’est pas inscrite auprès d’un utilisateur ou d’un ordinateur.  
  
 Une source de données de fichier rationalise le processus de connexion, car le fichier. DSN contient la chaîne de connexion qui devrait normalement être générée pour un appel à la fonction **SQLDriverConnect** . Un autre avantage du fichier. DSN est qu’il peut être copié sur n’importe quel ordinateur, de sorte que des sources de données identiques peuvent être utilisées par de nombreux ordinateurs à condition que le pilote approprié soit installé. Une source de données de fichier peut également être partagée par les applications. Une source de données de fichier partageable peut être placée sur un réseau et utilisée simultanément par plusieurs applications.  
  
 Un fichier. DSN peut également être non partagé. Un fichier. DSN non partageable réside sur un seul ordinateur et pointe vers une source de données de machine. Les sources de données de fichiers non partagées existent principalement pour permettre une conversion facile des sources de données de l’ordinateur en sources de données de fichier afin qu’une application puisse être conçue pour fonctionner uniquement avec des sources de données de fichier. Quand le gestionnaire de pilotes reçoit les informations contenues dans une source de données de fichier non partageable, il se connecte en fonction des besoins à la source de données de l’ordinateur vers laquelle pointe le fichier. DSN.  
  
 Pour plus d’informations sur les sources de données de fichier, consultez [connexion à l’aide de sources de données de fichier](../../odbc/reference/develop-app/connecting-using-file-data-sources.md)ou description de la fonction [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) .
