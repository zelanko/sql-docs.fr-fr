---
title: Types de données Microsoft Access | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Access driver
- Jet-based ODBC drivers [ODBC], Access driver
- desktop database drivers [ODBC], Access driver
- Access driver [ODBC], data types
- access data types [ODBC]
- data types [ODBC], Access driver
ms.assetid: b537348a-bea0-4bd6-84a4-52a75292957f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b99fd70e0119aa01d384066aaa2f3b91eed152b4
ms.sourcegitcommit: 480961f14405dc0b096aa8009855dc5a2964f177
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2019
ms.locfileid: "54420174"
---
# <a name="microsoft-access-data-types"></a>Types de données Microsoft Access
Le tableau suivant montre les types de données Microsoft Access, types de données utilisés pour créer des tables et les types de données ODBC SQL.  
  
|Type de données Microsoft Access|Type de données (Create Table)|Type de données SQL ODBC|  
|--------------------------------|-------------------------------|------------------------|  
|BIGBINARY [1]|LONGBINARY|SQL_LONGVARBINARY|  
|BINARY|BINARY|SQL_BINARY|  
|BIT|BIT|SQL_BIT|  
|COMPTEUR|COMPTEUR|SQL_INTEGER|  
|Monétaire (Currency)|Monétaire (Currency)|SQL_NUMERIC|  
|DATE/HEURE|DATETIME|SQL_TIMESTAMP|  
|GUID|GUID|SQL_GUID|  
|BINAIRE LONGUE|LONGBINARY|SQL_LONGVARBINARY|  
|TEXTE LONG|LONGTEXT|SQL_LONGVARCHAR[2] SQL_WLONGVARCHAR[3]|  
|MEMO|LONGTEXT|SQL_LONGVARCHAR[2] SQL_WLONGVARCHAR[3]|  
|NOMBRE (taille du champ = unique)|UNIQUE|SQL_REAL|  
|NOMBRE (taille du champ = DOUBLE)|DOUBLE|SQL_DOUBLE|  
|NOMBRE (taille du champ = octet)|OCTET NON SIGNÉ|SQL_TINYINT|  
|NOMBRE (taille du champ = entier)|COURT|SQL_SMALLINT|  
|NOMBRE (taille du champ = entier LONG)|LONG|SQL_INTEGER|  
|NUMERIC|NUMERIC|SQL_NUMERIC|  
|OLE|LONGBINARY|SQL_LONGVARBINARY|  
|TEXT|VARCHAR|SQL_VARCHAR[1] SQL_WVARCHAR[2]|  
|VARBINARY|VARBINARY|SQL_VARBINARY|  
  
 [1] applications accès 4.0 uniquement. Longueur maximale de 4 000 octets. Comportement similaire à LONGBINARY.  
  
 [2] applications ANSI uniquement.  
  
 [3] Unicode et 4.0 de l’accès des applications uniquement.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** retourne des types de données ODBC. Il ne retourne pas tous les types de données Microsoft Access si plusieurs types de Microsoft Access est mappé vers le même type de données ODBC SQL. Toutes les conversions dans l’annexe D de la *de référence du programmeur ODBC* sont pris en charge pour les types de données SQL répertoriés dans le tableau précédent.  
  
 Le tableau suivant présente des limitations sur les types de données Microsoft Access.  
  
|Type de données|Description|  
|---------------|-----------------|  
|BINARY, VARBINARY et VARCHAR|Création d’une colonne BINARY, VARBINARY ou VARCHAR de zéro ou de longueur non spécifiée retourne en fait une colonne de 510 octets.|  
|BYTE|Même si un champ de numéro d’accès à Microsoft avec une taille égale à BYTE n’est pas signé, un nombre négatif peut être inséré dans le champ lorsque vous utilisez le pilote Microsoft Access.|  
|CHAR et VARCHAR LONGVARCHAR|Un littéral de chaîne de caractères peut contenir n’importe quel caractère ANSI (décimal 1-255). Utilisez consécutifs un double guillemet (") pour représenter un guillemet simple (').<br /><br /> Procédures doivent être utilisées pour passer des données de caractères lors de l’utilisation de n’importe quel caractère spécial dans une colonne de type de données de caractères.|  
|DATE|Valeurs de date doivent être délimités en fonction du format de date canonique ODBC ou délimitées par le séparateur de date/heure (« # »). Sinon, Microsoft Access traite la valeur comme une expression arithmétique et ne génère pas un avertissement ou une erreur.<br /><br /> Par exemple, la date « 5 mars 1996 » doit être représentée en tant que {d ' 1996-03-05 »} ou #03/05/1996 #; Sinon, si seul le 03/05/1993 est soumise, Microsoft Access évaluera cela en tant que 3 divisé par 5 divisé en 1996. Cette valeur est arrondi à l’entier 0, et étant donné que le zéro jour mappe à 1899-12-31, la date est utilisée.<br /><br /> Une barre verticale (&#124;) ne peut pas être utilisés dans une valeur de date, même si placé à l’arrière de guillemets.|  
|GUID|Type de données limité à Microsoft Access 4.0.|  
|NUMERIC|Type de données limité à Microsoft Access 4.0.|  
  
 Vous trouverez davantage de limites sur les types de données dans [Limitations des types de données](../../odbc/microsoft/data-type-limitations.md).
