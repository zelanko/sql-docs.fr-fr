---
title: Paramètres du projet (mappage de Type) (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 136fdf6d-657f-447b-af41-49bbc6e0e93e
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e0a11a0b49589c3763b5af67623c9e819038c217
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63231820"
---
# <a name="project-settings-type-mapping-mysqltosql"></a>Paramètres du projet (Mappage de type) (MySQLToSQL)
Les paramètres de mappage de Type de projet vous permettent de définir des mappages de type par défaut pour le projet SSMA.  

Mappage de type est disponible dans les boîtes de dialogue Paramètres du projet et les paramètres de projet par défaut :  
  
-   Utilisez la boîte de dialogue Paramètres du projet pour définir les options de configuration pour le projet actuel. Pour accéder aux paramètres de mappage de type, dans le menu Outils, sélectionnez les paramètres du projet, puis cliquez sur le mappage de Type dans le volet gauche.  
  
-   Utilisez la boîte de dialogue Paramètres du projet par défaut pour définir les options de configuration pour tous les projets. Pour accéder au mappage de type paramètres, dans le menu Outils, sélectionnez les paramètres de projet par défaut, type de projet de migration Sélectionnez pour lequel les paramètres sont requis pour être affiché / a été remplacée par **Version cible de Migration** liste déroulante, puis cliquez sur Type Mappage dans le volet gauche.  
  
## <a name="options"></a>Options  
  
##### <a name="source-type"></a>Type de source  
Il est le type de données MySQL, qui doit être mappé au type de données de base de données cible.  
  
##### <a name="target-type"></a>Type de cible  
Type de la base de données cible pour le type de données MySQL spécifié.  
  
##### <a name="add"></a>Ajouter  
Cliquez pour ajouter un type de données à la liste de mappage.  
  
##### <a name="edit"></a>Modifier  
Cliquez pour modifier le type de données sélectionné dans la liste de mappage.  
  
##### <a name="remove"></a>Supprimer  
Cliquez pour supprimer le mappage de type de données sélectionnée dans la liste de mappage.  
  
##### <a name="reset-to-default"></a>Rétablir les valeurs par défaut  
Cliquez pour réinitialiser la liste de mappage de type pour les valeurs par défaut SSMA.  
  
## <a name="type-mappings"></a>Mappages de types  
Le tableau suivant présente le mappage par défaut entre les types de données source et cible  
  
|||  
|-|-|  
|**Type de données de MySQL**|**Type de données SQL Server**|  
|BIGINT|BIGINT|  
|bigint [*.. 255]|BIGINT|  
|binary|binaire [1]|  
|binaire [valeur 0.. 1]|binaire [1]|  
|binaire [2..255]|binaire [*]|  
|bit|binaire [1]|  
|bits [0..8]|binaire [1]|  
|bits [17..24]|binaire [3]|  
|bits [25..32]|binaire [4]|  
|bits [33..40]|binaire [5]|  
|bits [41..48]|binaire [6]|  
|bits [49..56]|binaire [7]|  
|bits [57..64]|binary[8]|  
|bits [9..16]|binaire [2]|  
|objet BLOB|varbinary(max)|  
|objet BLOB de [valeur 0.. 1]|varbinary [1]|  
|objet BLOB [2..8000]|varbinary [*]|  
|objet BLOB [8001.. *]|varbinary(max)|  
|bool|bit|  
|booléenne|bit|  
|char|nchar[1]|  
|octets de char|binaire [1]|  
|octets de char [valeur 0.. 1]|binaire [1]|  
|octets de char [2..255]|binaire [*]|  
|Char [valeur 0.. 1]|nchar[1]|  
|Char [2..255]|nchar[*]|  
|caractère|nchar[1]|  
|caractère variable la [valeur 0.. 1]|nvarchar[1]|  
|caractère variable [2..255]|NVARCHAR|  
|caractère [valeur 0.. 1]|nchar[1]|  
|caractère [2..255]|nchar[*]|  
|date|date|  
|datetime|datetime2[0]|  
|dec|Décimal|  
|DEC [*.. 65]|decimal[*][0]|  
|DEC [*.. 65] [\*... 30]|decimal[*][\*]|  
|Décimal|Décimal|  
|Decimal [*.. 65]|decimal[*][0]|  
|Decimal [*.. 65] [\*... 30]|decimal[*][\*]|  
|double|float [53]|  
|double précision|float [53]|  
|double précision [*.. 255] [\*... 30]|numeric[*][\*]|  
|double [*.. 255] [\*... 30]|numeric[*][\*]|  
|fixe|numeric|  
|fixe [*.. 65] [\*... 30]|numeric[*][\*]|  
|FLOAT|float [24]|  
|float [*.. 255] [\*... 30]|numeric[*][\*]|  
|float [*.. 53]|float [53]|  
|INT|INT|  
|int [*.. 255]|INT|  
|entier|INT|  
|entier [*.. 255]|INT|  
|longblob|varbinary(max)|  
|longtext|nvarchar(max)|  
|mediumblob|varbinary(max)|  
|mediumint|INT|  
|mediumint [*.. 255]|INT|  
|mediumtext|nvarchar(max)|  
|national char|nchar[1]|  
|national char [valeur 0.. 1]|nchar[1]|  
|national char [2..255]|nchar[*]|  
|caractères nationaux|nchar[1]|  
|variable de caractères nationaux|nvarchar[1]|  
|caractères nationaux faire varier la [valeur 0.. 1]|nvarchar[1]|  
|caractères nationaux varying [2..4000]|nvarchar[*]|  
|variable de caractères nationaux [4001.. *]|nvarchar(max)|  
|caractères nationaux [valeur 0.. 1]|nchar[1]|  
|caractères nationaux [2..255]|nchar[*]|  
|national varchar|nvarchar[1]|  
|national varchar [valeur 0.. 1]|nvarchar[1]|  
|national varchar [2..4000]|nvarchar[*]|  
|national varchar [4001.. *]|nvarchar(max)|  
|NCHAR|nchar[1]|  
|NCHAR varchar|nvarchar[1]|  
|NCHAR, varchar [valeur 0.. 1]|nvarchar[1]|  
|NCHAR, varchar [2..4000]|nvarchar[*]|  
|NCHAR varchar [4001.. *]|nvarchar(max)|  
|NCHAR [valeur 0.. 1]|nchar[1]|  
|NCHAR [2..255]|nchar[*]|  
|numeric|numeric|  
|numérique [*.. 65]|numérique [*] [0]|  
|numérique [*.. 65] [\*... 30]|numeric[*][\*]|  
|NVARCHAR|nvarchar[1]|  
|nvarchar [valeur 0.. 1]|nvarchar[1]|  
|nvarchar [2..4000]|nvarchar[*]|  
|nvarchar [4001.. *]|nvarchar(max)|  
|REAL|float [53]|  
|réel [*.. 255] [\*... 30]|numeric[*][\*]|  
|série|BIGINT|  
|SMALLINT|SMALLINT|  
|smallint [*.. 255]|SMALLINT|  
|text|nvarchar(max)|  
|texte [valeur 0.. 1]|nvarchar[1]|  
|texte [2..4000]|nvarchar[*]|  
|texte [4001.. *]|nvarchar(max)|  
|time|time|  
|TIMESTAMP|datetime|  
|tinyblob|varbinary[255]|  
|TINYINT|SMALLINT|  
|tinyint [*.. 255]|SMALLINT|  
|tinytext|nvarchar[255]|  
|valeurs bigint non signées|BIGINT|  
|valeurs bigint non signées [*.. 255]|BIGINT|  
|dec non signé|Décimal|  
|non signé dec [*.. 65]|decimal[*][0]|  
|non signé dec [*.. 65] [\*... 30]|decimal[*][\*]|  
|décimal non signé|Décimal|  
|décimal non signé [*.. 65]|decimal[*][0]|  
|décimal non signé [*.. 65] [\*... 30]|decimal[*][\*]|  
|double non signé|float [53]|  
|double précision non signée|float [53]|  
|unsigned double précision [*.. 255] [\*... 30]|numeric[*][\*]|  
|unsigned double [*.. 255] [\*... 30]|numeric[*][\*]|  
|unsigned fixe|numeric|  
|unsigned fixe [*.. 65] [\*... 30]|numeric[*][\*]|  
|float non signé|float [24]|  
|non signé float [*.. 255] [\*... 30]|numeric[*][\*]|  
|non signé float [*.. 53]|float [53]|  
|nombre entier non signé|BIGINT|  
|unsigned int [*.. 255]|BIGINT|  
|entier non signé|BIGINT|  
|entier non signé [*.. 255]|BIGINT|  
|mediumint non signé|INT|  
|mediumint non signé [*.. 255]|INT|  
|numérique non signé|numeric|  
|numérique non signée [*.. 65]|numérique [*] [0]|  
|numérique non signée [*.. 65] [\*... 30]|numeric[*][\*]|  
|non signé réel|float [53]|  
|unsigned réel [*.. 255 [[\*... 30]|numeric[*][\*]|  
|smallint non signé|INT|  
|smallint non signé [*.. 255]|INT|  
|tinyint non signé|TINYINT|  
|tinyint non signée [*.. 255]|TINYINT|  
|varbinary [valeur 0.. 1]|varbinary [1]|  
|varbinary [2..8000]|varbinary [*]|  
|varbinary [8001.. *]|varbinary(max)|  
|varchar [valeur 0.. 1]|nvarchar[1]|  
|varchar [2..4000]|nvarchar[*]|  
|varchar[4001..*]|nvarchar(max)|  
|year|SMALLINT|  
|année [2..2]|SMALLINT|  
|année [4..4]|SMALLINT|  
  
##### <a name="add"></a>Ajouter  
Cliquez pour ajouter un type de données à la liste de mappage.  
  
##### <a name="edit"></a>Modifier  
Cliquez pour modifier un type de données dans la liste de mappage.  
  
##### <a name="remove"></a>Supprimer  
Cliquez pour supprimer le mappage de type de données sélectionnée dans la liste de mappage.  
  
##### <a name="reset-to-default"></a>Rétablir les valeurs par défaut  
Cliquez pour réinitialiser tous les mappages de type de données pour les valeurs par défaut SSMA.  
  
