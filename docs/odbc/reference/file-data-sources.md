---
title: Sources de données de fichiers | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 733b958ee883aa62034b4acc1eec67100b35a74d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62628452"
---
# <a name="file-data-sources"></a>Sources de données de fichier
*Sources de données de fichiers* sont stockées dans un fichier et d’autoriser les informations de connexion à utiliser à plusieurs reprises par un utilisateur unique ou partagée par plusieurs utilisateurs. Lorsqu’une source de données de fichier est utilisée, le Gestionnaire de pilotes établit la connexion à la source de données en utilisant les informations dans un fichier .dsn. Ce fichier peut être manipulé comme tout autre fichier. Une source de données de fichier n’a pas un nom de source de données, comme le fait d’une source de données machine et n’est pas inscrit à n’importe quel ordinateur ou un utilisateur.  
  
 Une source de données fichier rationalise le processus de connexion, car le fichier .dsn contient la chaîne de connexion qui aurait sinon générés pour un appel à la **SQLDriverConnect** (fonction). Un autre avantage du fichier .dsn est qu’il peut être copié à n’importe quel ordinateur, afin de sources de données identiques peuvent être utilisées par nombreux ordinateurs tant qu’ils ont le pilote approprié installé. Une source de données de fichier peut également être partagée par les applications. Une source de données fichier partageable peut être placée sur un réseau et utilisée simultanément par plusieurs applications.  
  
 Un fichier .dsn peut également être partageable. Un fichier .dsn partageable réside sur un seul ordinateur et pointe vers une source de données machine. Sources de données fichier partageable existent principalement pour permettre la conversion facile des sources de données aux sources de données de fichier afin qu’une application peut être conçue pour fonctionner uniquement avec les fichiers sources de données. Lorsque le Gestionnaire de pilotes est envoyé les informations dans une source de données fichier partageable, il se connecte que nécessaire pour la source de données d’ordinateur vers lequel pointe le fichier .dsn.  
  
 Pour plus d’informations sur les fichiers sources de données, consultez [se connectant à l’aide de fichiers Sources de données](../../odbc/reference/develop-app/connecting-using-file-data-sources.md), ou le [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) description de fonction.
