---
title: Paramètres du projet (mappage de Type) (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: cf426c69-6a8e-4d19-951d-6661d5ae2562
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 91498db5535c99c7c8afaba85efc35639510a079
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63270007"
---
# <a name="project-settings-type-mapping-db2tosql"></a>Paramètres du projet (mappage de Type) (DB2ToSQL)
La page mappage de Type de la **paramètres du projet** boîte de dialogue contient les paramètres qui personnalisent comment SSMA convertit les types de données DB2 dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données.  
  
La page mappage de Type est disponible dans le **paramètres du projet** et **par défaut des paramètres de projet** boîtes de dialogue.  
  
-   Pour spécifier les paramètres pour tous les futurs projets SSMA, sur le **outils** menu, cliquez sur **par défaut des paramètres de projet**, sélectionnez le type de projet de migration pour lequel les paramètres sont requis pour être affichées ou modifiées à partir de **Version cible de migration** liste déroulante, puis cliquez sur **le mappage de Type** en bas du volet gauche.  
  
-   Pour spécifier les paramètres pour le projet actuel, sur le **outils** menu, cliquez sur **paramètres du projet**, puis cliquez sur **le mappage de Type** en bas du volet gauche.  
  
Pour spécifier les paramètres pour l’objet actuel ou la classe d’objets, utilisez le **le mappage de Type** onglet dans la fenêtre SSMA principale.  
  
## <a name="options"></a>Options  
Le tableau suivant présente le **le mappage de Type** onglet options :  
  
**Type de source**  
Le type de données DB2 mappé.  
  
**Type de cible**  
La cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données pour le type de données DB2 spécifié.  
  
Consultez les tableaux dans la section suivante pour la valeur par défaut SSMA pour DB2 les mappages de types.  
  
**Ajouter**  
Cliquez pour ajouter un type de données à la liste de mappage.  
  
**Modifier**  
Cliquez pour modifier le type de données sélectionné dans la liste de mappage.  
  
**Supprimer**  
Cliquez pour supprimer le mappage de type de données sélectionnée dans la liste de mappage.  
  
**Rétablir les valeurs par défaut**  
Cliquez pour réinitialiser la liste de mappage de type pour les valeurs par défaut SSMA.  
  
## <a name="default-type-mappings"></a>Mappages de Type par défaut  
Dans SSMA pour DB2, vous pouvez définir des mappages de types personnalisés pour les arguments, les colonnes, les variables locales et les valeurs de retour. Le mappage par défaut pour les arguments et les types de retour est presque identique.  
  
### <a name="default-argument-type-and-return-value-type-mapping"></a>Type d’Argument par défaut et de retourner le mappage de Type de valeur  
Le tableau suivant contient le mappage de type de données par défaut pour les arguments et valeurs de retour.  
  
|DB2 Type de données|Par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Type de données|  
|-----------------|-------------------------------------------------------------------------|  
|BFILE|varbinary(max)|  
|binary_double|float [53]|  
|binary_float|float [53]|  
|binary_integer|INT|  
|objet BLOB|varbinary(max)|  
|boolean|bit|  
|char|varchar(max)|  
|char varying|varchar(max)|  
|caractère|varchar(max)|  
|character varying|varchar(max)|  
|CLOB|varchar(max)|  
|date|datetime2[0]|  
|dec|dec[38][0]|  
|Décimal|float [53]|  
|double précision|float [53]|  
|FLOAT|float [53]|  
|INT|INT|  
|entier|INT|  
|long|varchar(max)|  
|long raw|varbinary(max)|  
|long raw [\*... 8000]<sup>\*</sup>|varbinary[\*]|  
|long raw [8001..\*]<sup>\*</sup>|varbinary(max)|  
|national char|nvarchar(max)|  
|national char varying|nvarchar(max)|  
|caractères nationaux|nvarchar(max)|  
|variable de caractères nationaux<sup>\*\*</sup>|nvarchar(max)|  
|variable de caractères nationaux<sup>\*</sup>|nvarchar(max)|  
|NCHAR|nvarchar(max)|  
|nclob|nvarchar(max)|  
|nombre|float [53]|  
|numeric|float [53]|  
|nvarchar2|nvarchar(max)|  
|pls_integer|INT|  
|brut|varbinary(max)|  
|REAL|float [53]|  
|ID de ligne|UNIQUEIDENTIFIER|  
|signtype|SMALLINT|  
|SMALLINT|SMALLINT|  
|chaîne|varchar(max)|  
|TIMESTAMP|datetime2|  
|horodateur avec fuseau horaire local|datetimeoffset|  
|horodateur avec fuseau horaire|datetimeoffset|  
|UROWID|UNIQUEIDENTIFIER|  
|varchar|varchar(max)|  
|varchar2|varchar(max)|  
|xmltype|Xml|  
  
<sup>\*</sup> S’applique pour retourner la valeur le mappage de type uniquement.  
  
<sup>\*\*</sup> S’applique à l’argument le mappage de type uniquement.  
  
### <a name="default-column-type-mapping"></a>Mappage de Type de colonne par défaut  
Le tableau suivant contient le mappage de type par défaut pour les colonnes.  
  
|DB2 Type de données|Par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Type de données|  
|-----------------|-------------------------------------------------------------------------|  
|BFILE|varbinary(max)|  
|binary_double|float [53]|  
|binary_float|float [53]|  
|objet BLOB|varbinary(max)|  
|char|char|  
|char varying [\*... \*]|varchar[\*]|  
|char[\*..\*]|char[\*]|  
|caractère|char|  
|variable de caractère [\*... \*]|varchar[\*]|  
|caractère [\*... \*]|char[\*]|  
|CLOB|varchar(max)|  
|date|datetime2[0]|  
|dec|dec[38][0]|  
|dec[\*..\*]|dec[\*][0]|  
|dec[\*..\*][\*..\*]|dec[\*][\*]|  
|Décimal|decimal[38][0]|  
|decimal[\*..\*]|decimal[\*][0]|  
|decimal[\*..\*][\*..\*]|decimal[\*][\*]|  
|double précision|float [53]|  
|FLOAT|float [53]|  
|float [\*... 53]|float[\*]|  
|float [54..\*]|float [53]|  
|INT|INT|  
|entier|INT|  
|long|varchar(max)|  
|long raw|varbinary(max)|  
|long raw [\*... 8000]|varbinary[\*]|  
|long raw [8001..\*]|varbinary(max)|  
|long varchar|varchar(max)|  
|long [\*... 8000]|varchar[\*]|  
|long[8001..\*]|varchar(max)|  
|national char|NCHAR|  
|national char varying [\*... \*]|nvarchar[\*]|  
|national char [\*... \*]|nchar[\*]|  
|caractères nationaux|NCHAR|  
|variable de caractères nationaux [\*... \*]|nvarchar[\*]|  
|les caractères nationaux [\*... \*]|nchar[\*]|  
|NCHAR|NCHAR|  
|nchar[\*]|nchar[\*]|  
|nclob|nvarchar(max)|  
|nombre|float [53]|  
|nombre [\*... \*]|numeric[\*]|  
|nombre [\*... \*][\*.. \*]|numeric[\*][\*]|  
|numeric|numeric|  
|numérique [\*... \*]|numeric[\*]|  
|numeric[\*..\*][\*..\*]|numeric[\*][\*]|  
|nvarchar2[\*..\*]|nvarchar[\*]|  
|raw[\*..\*]|varbinary[\*]|  
|REAL|float [53]|  
|ID de ligne|UNIQUEIDENTIFIER|  
|SMALLINT|SMALLINT|  
|TIMESTAMP|datetime2|  
|horodateur avec fuseau horaire local|datetimeoffset|  
|horodateur avec fuseau horaire local [\*... \*]|datetimeoffset[\*]|  
|horodateur avec fuseau horaire|datetimeoffset|  
|horodateur avec fuseau horaire [\*... \*]|datetimeoffset[\*]|  
|horodatage [\*... \*]|datetime2[\*]|  
|UROWID|UNIQUEIDENTIFIER|  
|urowid[\*..\*]|UNIQUEIDENTIFIER|  
|varchar[\*..\*]|varchar[\*]|  
|varchar2[\*..\*]|varchar[\*]|  
|Xmltype|Xml|  
  
### <a name="default-local-variable-type-mapping"></a>Mappage de Type de Variable locale par défaut  
Le tableau suivant contient le mappage de type par défaut pour les variables locales.  
  
|DB2 Type de données|Par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Type de données|  
|-----------------|-------------------------------------------------------------------------|  
|Bfile|varbinary(max)|  
|binary_double|float [53]|  
|binary_float|float [53]|  
|binary_interger|INT|  
|Objet blob|varbinary(max)|  
|Booléen|bit|  
|Char|char|  
|char varying [\*... 8000]|varchar[\*]|  
|char varying [8001..\*]|varchar(max)|  
|Char [\*... 8000]|char[\*]|  
|char[8001..\*]|varchar(max)|  
|Caractère|char|  
|variable de caractère [\*... 8000]|varchar[\*]|  
|variable de caractère [8001..\*]|varchar(max)|  
|caractère [\*... 8000]|char[\*]|  
|caractère [8001..\*]|varchar(max)|  
|CLOB|varchar(max)|  
|date|datetime2[0]|  
|dec|dec[38][0]|  
|dec[\*..\*]|dec[\*][0]|  
|dec[\*..\*][\*..\*]|dec[\*][\*]|  
|Décimal|decimal[38][0]|  
|decimal[\*..\*]|decimal[\*][0]|  
|decimal[\*..\*][\*..\*]|decimal[\*][\*]|  
|double précision|float [53]|  
|float|float [53]|  
|float [\*... 53]|float[\*]|  
|float [54..\*]|float [53]|  
|Int|INT|  
|Entier|INT|  
|entier [\*... \*]|numeric[\*][0]|  
|Long|varchar(max)|  
|long raw|varbinary(max)|  
|long raw [\*... 8000]|varbinary[\*]|  
|long raw [8001..\*]|varbinary(max)|  
|national char|NCHAR|  
|national char varying [\*... 4000]|nvarchar[\*]|  
|national char varying [4001..\*]|nvarchar(max)|  
|national char [\*... 4000]|nchar[\*]|  
|national char [4001..\*]|nvarchar(max)|  
|caractères nationaux|NCHAR|  
|les caractères nationaux [\*... 4000]|nvarchar[\*]|  
|les caractères nationaux [4001..\*]|nvarchar(max)|  
|variable de caractères nationaux [\*... 4000]|nvarchar[\*]|  
|variable de caractères nationaux [4001..\*]|nvarchar(max)|  
|Nchar|NCHAR|  
|nchar[\*..4000]|nchar[\*]|  
|nchar[4001..\*]|nvarchar(max)|  
|NCHAR varying [\*... 4000]|nvarchar[\*]|  
|NCHAR varying [4001..\*]|nvarchar(max)|  
|NCLOB|nvarchar(max)|  
|Number|float [53]|  
|nombre [\*... \*]|numeric[\*]|  
|nombre [\*... \*][\*.. \*]|numeric[\*][\*]|  
|Numeric|numérique [38] [0]|  
|numérique [\*... \*]|numeric[\*]|  
|numeric[\*..\*][\*..\*]|numeric[\*][\*]|  
|nvarchar2[\*..4000]|nvarchar[\*]|  
|nvarchar2[4001..\*]|nvarchar(max)|  
|pls_integer|INT|  
|brut [\*... 8000]|varbinary[\*]|  
|brut [8001..\*]|varbinary(max)|  
|Real|float [53]|  
|Rowid|UNIQUEIDENTIFIER|  
|Signtype|SMALLINT|  
|Smallint|SMALLINT|  
|chaîne [\*... 8000]|varchar[\*]|  
|chaîne [8001..\*]|varchar(max)|  
|TIMESTAMP|datetime2|  
|horodateur avec fuseau horaire local|datetimeoffset|  
|horodateur avec fuseau horaire|datetimeoffset|  
|horodateur avec fuseau horaire local [\*... \*]|datetimeoffset[\*]|  
|horodateur avec fuseau horaire [\*... \*]|datetimeoffset[\*]|  
|horodatage [\*... \*]|datetime2[\*]|  
|UROWID|UNIQUEIDENTIFIER|  
|urowid[\*..\*]|UNIQUEIDENTIFIER|  
|varchar[\*..8000]|varchar[\*]|  
|varchar[8001..\*]|varchar(max)|  
|VARCHAR2 [\*... 8000]|varchar[\*]|  
|varchar2[8001..\*]|varcha(max)|  
|Xmltype|Xml|  
  
## <a name="see-also"></a>Voir aussi  
[Référence de l’Interface utilisateur &#40;DB2ToSQL&#41;](../../ssma/db2/user-interface-reference-db2tosql.md)  
  
