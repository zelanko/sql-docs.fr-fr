---
title: Compatibilité des pilotes de base de données Bureau | Microsoft Docs
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
ms.openlocfilehash: 31263162526b6bd2e0a116a473f09f9e2caeba94
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68077284"
---
# <a name="desktop-database-driver-compatibility"></a>Compatibilité des pilotes pour les bases de données de poste de travail
Unicode est une méthode d’encodage de caractères logiciels qui traite tous les caractères comme ayant une largeur fixe de deux octets. Cette méthode est utilisée comme alternative à l’encodage de caractères ANSI Windows, car elle représente les caractères d’un octet, est limitée à 256 caractères. Étant donné que le format Unicode peut représenter plus de 65 000 caractères, il prend en charge de nombreux langages dont les caractères ne sont pas représentés dans l’encodage ANSI.  
  
 Le gestionnaire de pilotes ODBC 3,5 (ou version ultérieure) est compatible Unicode. Cela affecte deux domaines majeurs : les appels de fonction et les types de données de chaîne. Le gestionnaire de pilotes mappe les arguments de chaîne de fonction et les données de chaîne selon les exigences de l’application et du pilote, qui peuvent être compatibles Unicode ou ANSI.  
  
 Le gestionnaire de pilotes ODBC 3,5 (ou version ultérieure) prend en charge l’utilisation d’un pilote Unicode avec une application Unicode et une application ANSI. Il prend également en charge l’utilisation d’un pilote ANSI avec une application ANSI. Le gestionnaire de pilotes fournit un mappage Unicode-à-ANSI limité pour une application Unicode utilisant un pilote ANSI. Cela permet l’accès aux bases de données Jet 3,5 et la prise en charge de tous les types de fichiers ISAM existants.  
  
 Quand une application ANSI utilise le pilote de base de données du Bureau ODBC 4,0 et accède à Microsoft Access 4,0 ou version ultérieure, le pilote expose le type de données en tant que SQL_CHAR, SQL_VARCHAR ou SQL_LONGVARCHAR même si Jet 4,0 prend en charge la version étendue. Les versions antérieures de jet ne prennent pas en charge SQL_WCHAR, SQL_WVARCHAR et SQL_WLONGVARCHAR. Cette restriction s’applique également dans les cas où les anciens formats sont utilisés avec le Moteur de base de données Jet 4,0.  
  
 Pour plus d’informations sur les problèmes Unicode liés à ODBC, consultez [Unicode](../../odbc/reference/develop-app/unicode.md) dans considérations sur la programmation.
