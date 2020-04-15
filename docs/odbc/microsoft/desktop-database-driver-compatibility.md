---
title: Compatibilité des pilotes de base de données de bureau (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 89eea7ab112eaefdc73c7cbc72ee3555797c7efd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303520"
---
# <a name="desktop-database-driver-compatibility"></a>Compatibilité des pilotes pour les bases de données de poste de travail
Unicode est une méthode d’encodage de caractère logiciel qui traite tous les personnages comme ayant une largeur fixe de deux octets. Cette méthode est utilisée comme une alternative à l’encodage de caractères de Windows ANSI, qui, parce qu’il représente des caractères dans un byte, est limité à 256 caractères. Parce qu’Unicode peut représenter plus de 65 000 caractères, il accueille de nombreuses langues dont les personnages ne sont pas représentés dans l’encodage de l’ANSI.  
  
 L’ODBC 3.5 (ou plus tard) Driver Manager est compatible Unicode. Cela affecte deux domaines principaux : les appels de fonction et les types de données de chaîne. Le Driver Manager cartographie les arguments de chaîne de fonction et les données de chaîne comme l’exige l’application et le pilote, qui peuvent être soit compatibles Unicode ou SANS permis.  
  
 L’ODBC 3.5 (ou plus tard) Driver Manager prend en charge l’utilisation d’un pilote Unicode avec une application Unicode et une application ANSI. Il soutient également l’utilisation d’un pilote ANSI avec une application ANSI. Le Driver Manager fournit une cartographie Unicode-à-ANSI limitée pour une application Unicode travaillant avec un pilote ANSI. Cela permet d’accéder aux bases de données Jet 3.5 et de prendre en charge tous les types de fichiers ISAM existants.  
  
 Lorsqu’une application ANSI utilise le pilote de base de données de bureau ODBC 4.0 et accède à Microsoft Access 4.0 ou plus tard, le pilote expose le type de données comme SQL_CHAR, SQL_VARCHAR ou SQL_LONGVARCHAR même si Jet 4.0 prend en charge la version large. Les anciennes versions de Jet ne prennent pas en charge SQL_WCHAR, SQL_WVARCHAR et SQL_WLONGVARCHAR. Cette restriction s’applique également dans les cas où les anciens formats sont utilisés avec le moteur de base de données Jet 4.0.  
  
 Pour plus d’informations sur les problèmes d’Unicode avec ODBC, voir [Unicode](../../odbc/reference/develop-app/unicode.md) dans Programming Considerations.
