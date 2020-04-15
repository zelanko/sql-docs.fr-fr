---
title: Sources de données de fichiers (en anglais seulement) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306650"
---
# <a name="file-data-sources"></a>Sources de données de fichier
*Les sources de données* de fichiers sont stockées dans un fichier et permettent d’utiliser à plusieurs reprises les informations de connexion par un seul utilisateur ou partagées entre plusieurs utilisateurs. Lorsqu’une source de données de fichiers est utilisée, le gestionnaire de pilote effectue la connexion à la source de données en utilisant les informations contenues dans un fichier .dsn. Ce fichier peut être manipulé comme n’importe quel autre fichier. Une source de données de fichiers n’a pas de nom de source de données, tout comme une source de données de machine, et n’est enregistrée à aucun utilisateur ou machine.  
  
 Une source de données de fichiers rationalise le processus de connexion, car le fichier .dsn contient la chaîne de connexion qui devrait autrement être construite pour un appel à la fonction **SQLDriverConnect.** Un autre avantage du fichier .dsn est qu’il peut être copié à n’importe quelle machine, de sorte que des sources de données identiques peuvent être utilisées par de nombreuses machines tant qu’ils ont le conducteur approprié installé. Une source de données de fichiers peut également être partagée par des applications. Une source de données de fichiers partageable peut être placée sur un réseau et utilisée simultanément par plusieurs applications.  
  
 Un fichier .dsn peut également être inshareable. Un fichier .dsn inshareable se trouve sur une seule machine et indique une source de données de machine. Des sources de données de fichiers non partageables existent principalement pour permettre la conversion facile des sources de données de machines pour déposer des sources de données afin qu’une application puisse être conçue uniquement pour fonctionner uniquement avec les sources de données de fichiers. Lorsque le gestionnaire de pilote reçoit les informations dans une source de données de fichiers non partageable, il se connecte au besoin à la source de données de la machine à laquelle le fichier .dsn indique.  
  
 Pour plus d’informations sur les sources de données de fichiers, voir [Connecting Using File Data Sources](../../odbc/reference/develop-app/connecting-using-file-data-sources.md), ou la description de la fonction [SQLDriverConnect.](../../odbc/reference/syntax/sqldriverconnect-function.md)
