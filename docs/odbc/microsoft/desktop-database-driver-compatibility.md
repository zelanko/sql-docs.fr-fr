---
title: Compatibilité des pilotes de base de données de bureau | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], Unicode
- Unicode [ODBC], desktop database drivers
- ODBC desktop database drivers [ODBC], Unicode
- backward compatibility [ODBC], Unicode
- desktop database drivers [ODBC], Unicode
- Jet-based ODBC drivers [ODBC], Unicode
ms.assetid: dd695638-1a0b-4e27-8a6a-9510ebb5a5ee
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d081d53458ec59eb2ac9f05c5c1d47d6991b5010
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63240359"
---
# <a name="desktop-database-driver-compatibility"></a>Compatibilité des pilotes pour les bases de données de poste de travail
Unicode est une méthode d’encodage de caractères logiciel traite tous les caractères comme ayant une largeur fixe de deux octets. Cette méthode est utilisée comme alternative à l’encodage de caractères Windows ANSI, c'est-à-dire, car il représente les caractères dans un seul octet, limitée à 256 caractères. Étant donné que Unicode peut représenter plus de 65 000 caractères, il prend en charge de nombreuses langues dont les caractères ne sont pas représentées au format ANSI.  
  
 Le Gestionnaire de pilotes ODBC 3.5 (ou version ultérieure) prend en charge Unicode. Cela affecte les deux domaines majeurs : appels de fonction et les types de données string. Les arguments de chaîne de gestionnaire de pilotes maps (fonction) et les données de type chaîne comme requis par l’application et le pilote, qui peuvent être compatibles Unicode soit compatible ANSI.  
  
 Le Gestionnaire de pilotes ODBC 3.5 (ou version ultérieure) prend en charge l’utilisation d’un pilote d’Unicode avec une application Unicode et une application ANSI. Il prend également en charge l’utilisation d’un pilote ANSI avec une application ANSI. Le Gestionnaire de pilotes offre limitée mappage Unicode en ANSI pour une application Unicode fonctionne avec un pilote ANSI. Cela permet d’accéder aux bases de données Jet 3.5 et prise en charge de tous les types de fichier ISAM existants.  
  
 Quand une application ANSI utilise le pilote de base de données ODBC Desktop 4.0 et accède à Microsoft Access 4.0 ou une version ultérieure, le pilote expose le type de données en tant que SQL_CHAR, SQL_VARCHAR ou SQL_LONGVARCHAR même si Jet 4.0 prend en charge la version large. Les versions antérieures de Jet ne prennent pas en charge SQL_WCHAR, SQL_WVARCHAR et SQL_WLONGVARCHAR. Cette restriction s’applique également dans les cas où les anciens formats sont utilisés avec le moteur de base de données Jet 4.0.  
  
 Pour plus d’informations concernant les problèmes d’Unicode avec ODBC, consultez [Unicode](../../odbc/reference/develop-app/unicode.md) dans les considérations sur la programmation.
