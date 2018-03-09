---
title: "Paramètres (Type de mappage) du projet (OracleToSQL) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bb8466e-2199-4f00-8513-b04e9586723d
caps.latest.revision: 
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: f4be0d12ce3067f46c934cfa7e053ddd1779ac9f
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="project-settings-type-mapping-oracletosql"></a>Paramètres (Type de mappage) du projet (OracleToSQL)
La page mappage de Type de la **les paramètres de projet** boîte de dialogue contient des paramètres permettant de personnaliser comment SSMA convertit les types de données Oracle dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] des types de données.  
  
La page mappage de Type est disponible dans le **les paramètres de projet** et **les paramètres de projet par défaut** boîtes de dialogue.  
  
-   Pour spécifier les paramètres pour tous les futurs projets SSMA, sur le **outils** menu, cliquez sur **par défaut des paramètres de projet**, sélectionnez le type de projet de migration pour lequel les paramètres sont requis pour être affichées ou modifiées à partir de **Version cible de la Migration** liste déroulante, puis cliquez sur **le mappage de Type** en bas du volet gauche.  
  
-   Pour spécifier les paramètres pour le projet actuel, sur le **outils** menu, cliquez sur **les paramètres de projet**, puis cliquez sur **le mappage de Type** en bas du volet gauche.  
  
Pour spécifier les paramètres pour l’objet en cours ou de la classe d’objets, utilisez la **le mappage de Type** onglet dans la fenêtre principale de SSMA.  
  
## <a name="options"></a>Options  
Le tableau suivant présente la **le mappage de Type** onglet options :  
  
**Type de source**  
Le type de données Oracle mappé.  
  
Type de cible  
La cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] type de données pour le type de données Oracle spécifié.  
  
Consultez les tableaux dans la section suivante pour la valeur par défaut SSMA pour les mappages de type Oracle.  
  
**Ajouter**  
Cliquez pour ajouter un type de données à la liste de mappage.  
  
**Modifier**  
Cliquez pour modifier le type de données sélectionné dans la liste de mappage.  
  
**Supprimer**  
Cliquez pour supprimer le mappage de type de données sélectionnées à partir de la liste de mappage.  
  
**Réinitialiser les valeurs par défaut**  
Cliquez pour réinitialiser la liste de mappage de type pour les valeurs par défaut SSMA.  
  
## <a name="default-type-mappings"></a>Mappages de Type par défaut  
Dans SSMA pour Oracle, vous pouvez définir des mappages de types personnalisés pour les arguments, les colonnes, les variables locales et les valeurs de retour. Le mappage par défaut pour les arguments et les types de retour est presque identique.  
  
### <a name="default-argument-type-and-return-value-type-mapping"></a>Type d’Argument par défaut et le mappage de Type de valeur de retour  
Le tableau suivant contient le mappage de type de données par défaut pour les arguments et valeurs de retour.  
  
|Type de données Oracle|Par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Type de données|  
|--------------------|-------------------------------------------------------------------------|  
|bfile|varbinary(max)|  
|binary_double|float[53]|  
|binary_float|float[53]|  
|binary_integer|int|  
|objet BLOB|varbinary(max)|  
|boolean|bit|  
|char|varchar(max)|  
|char varying|varchar(max)|  
|caractère|varchar(max)|  
|character varying|varchar(max)|  
|CLOB|varchar(max)|  
|date|datetime2[0]|  
|dec|dec[38][0]|  
|Décimal|float[53]|  
|double précision|float[53]|  
|float|float[53]|  
|int|int|  
|entier|int|  
|long|varchar(max)|  
|long raw|varbinary(max)|  
|long raw [\*... 8000]<sup>*</sup>|varbinary[*]|  
|long raw [8001..\*]<sup>*</sup>|varbinary(max)|  
|national char|nvarchar(max)|  
|national char varying|nvarchar(max)|  
|caractères nationaux|nvarchar(max)|  
|variable de caractères nationaux<sup>**</sup>|nvarchar(max)|  
|variable de caractères nationaux<sup>*</sup>|nvarchar(max)|  
|NCHAR|nvarchar(max)|  
|NCLOB|nvarchar(max)|  
|nombre|float[53]|  
|numérique|float[53]|  
|nvarchar2|nvarchar(max)|  
|pls_integer|int|  
|brut|varbinary(max)|  
|real|float[53]|  
|ID de ligne|uniqueidentifier|  
|Signtype|smallint|  
|smallint|smallint|  
|chaîne|varchar(max)|  
|TIMESTAMP|datetime2|  
|horodateur avec fuseau horaire local|datetimeoffset|  
|horodateur avec fuseau horaire|datetimeoffset|  
|UROWID|uniqueidentifier|  
|varchar|varchar(max)|  
|varchar2|varchar(max)|  
|xmltype|xml|  
  
<sup>*</sup> S’applique pour retourner la valeur type mappage uniquement.  
  
<sup>**</sup> S’applique à l’argument de type mappage uniquement.  
  
### <a name="default-column-type-mapping"></a>Mappage de Type de colonne par défaut  
Le tableau suivant contient le mappage de type par défaut pour les colonnes.  
  
|Type de données Oracle|Par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Type de données|  
|--------------------|-------------------------------------------------------------------------|  
|bfile|varbinary(max)|  
|binary_double|float[53]|  
|binary_float|float[53]|  
|objet BLOB|varbinary(max)|  
|char|char|  
|char varying [*.. \*]|varchar[*]|  
|Char [*.. \*]|char[*]|  
|caractère|char|  
|variable de caractères [*.. \*]|varchar[*]|  
|caractère [*.. \*]|char[*]|  
|CLOB|varchar(max)|  
|date|datetime2[0]|  
|dec|dec[38][0]|  
|DEC [*.. \*]|dec[*][0]|  
|dec[*..\*][\*..\*]|dec[*][\*]|  
|Décimal|decimal[38][0]|  
|decimal[*..\*]|decimal[*][0]|  
|decimal[*..\*][\*..\*]|decimal[*][\*]|  
|double précision|float[53]|  
|float|float[53]|  
|float[*..53]|float[*]|  
|float [54.. *]|float[53]|  
|int|int|  
|entier|int|  
|long|varchar(max)|  
|long raw|varbinary(max)|  
|long raw [*.. 8000]|varbinary[*]|  
|long raw [8001.. *]|varbinary(max)|  
|long varchar|varchar(max)|  
|long [*.. 8000]|varchar[*]|  
|long[8001..*]|varchar(max)|  
|national char|NCHAR|  
|national char varying [*.. \*]|nvarchar[*]|  
|national char [*.. \*]|nchar[*]|  
|caractères nationaux|NCHAR|  
|variable de caractères nationaux [*.. \*]|nvarchar[*]|  
|les caractères nationaux [*.. \*]|nchar[*]|  
|NCHAR|NCHAR|  
|nchar[*]|nchar[*]|  
|NCLOB|nvarchar(max)|  
|nombre|float[53]|  
|nombre [*.. \*]|numeric[*]|  
|number[*..\*][\*..\*]|numeric[*][\*]|  
|numérique|numérique|  
|numérique [*.. \*]|numeric[*]|  
|numeric[*..\*][\*..\*]|numeric[*][\*]|  
|nvarchar2[*..\*]|nvarchar[*]|  
|RAW [*.. \*]|varbinary[*]|  
|real|float[53]|  
|ID de ligne|uniqueidentifier|  
|smallint|smallint|  
|TIMESTAMP|datetime2|  
|horodateur avec fuseau horaire local|datetimeoffset|  
|horodateur avec fuseau horaire local [*.. \*]|datetimeoffset[*]|  
|horodateur avec fuseau horaire|datetimeoffset|  
|horodateur avec fuseau horaire [*.. \*]|datetimeoffset[*]|  
|timestamp[*..\*]|datetime2[*]|  
|UROWID|uniqueidentifier|  
|UROWID [*.. \*]|uniqueidentifier|  
|varchar[*..\*]|varchar[*]|  
|varchar2[*..\*]|varchar[*]|  
|Xmltype|xml|  
  
### <a name="default-local-variable-type-mapping"></a>Mappage de Type de Variable locale par défaut  
Le tableau suivant contient le mappage de type par défaut pour les variables locales.  
  
|Type de données Oracle|Par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Type de données|  
|--------------------|-------------------------------------------------------------------------|  
|Bfile|varbinary(max)|  
|binary_double|float[53]|  
|binary_float|float[53]|  
|binary_interger|int|  
|Blob|varbinary(max)|  
|Booléen|bit|  
|Char|char|  
|char varying [*.. 8000]|varchar[*]|  
|char varying [8001.. *]|varchar(max)|  
|Char [*.. 8000]|char[*]|  
|char[8001..*]|varchar(max)|  
|Caractère|char|  
|variable de caractères [*.. 8000]|varchar[*]|  
|variable de caractères [8001.. *]|varchar(max)|  
|caractère [*.. 8000]|char[*]|  
|caractère [8001.. *]|varchar(max)|  
|CLOB|varchar(max)|  
|date|datetime2[0]|  
|dec|dec[38][0]|  
|DEC [*.. \*]|dec[*][0]|  
|dec[*..\*][\*..\*]|dec[*][\*]|  
|Décimal|decimal[38][0]|  
|decimal[*..\*]|decimal[*][0]|  
|decimal[*..\*][\*..\*]|decimal[*][\*]|  
|double précision|float[53]|  
|Float|float[53]|  
|float[*..53]|float[*]|  
|float [54.. *]|float[53]|  
|Int|int|  
|Entier|int|  
|entier [*.. \*]|numeric[*][0]|  
|Long|varchar(max)|  
|long raw|varbinary(max)|  
|long raw [*.. 8000]|varbinary[*]|  
|long raw [8001.. *]|varbinary(max)|  
|national char|NCHAR|  
|national char varying [*.. 4000]|nvarchar[*]|  
|national char varying [4001.. *]|nvarchar(max)|  
|national char [*.. 4000]|nchar[*]|  
|national char [4001.. *]|nvarchar(max)|  
|caractères nationaux|NCHAR|  
|les caractères nationaux [*.. 4000]|nvarchar[*]|  
|les caractères nationaux [4001.. *]|nvarchar(max)|  
|variable de caractères nationaux [*.. 4000]|nvarchar[*]|  
|variable de caractères nationaux [4001.. *]|nvarchar(max)|  
|Nchar|NCHAR|  
|nchar[*..4000]|nchar[*]|  
|nchar[4001..*]|nvarchar(max)|  
|NCHAR varying [*.. 4000]|nvarchar[*]|  
|NCHAR varying [4001.. *]|nvarchar(max)|  
|NCLOB|nvarchar(max)|  
|Number|float[53]|  
|nombre [*.. \*]|numeric[*]|  
|number[*..\*][\*..\*]|numeric[*][\*]|  
|Numérique|numeric[38][0]|  
|numérique [*.. \*]|numeric[*]|  
|numeric[*..\*][\*..\*]|numeric[*][\*]|  
|nvarchar2[*..4000]|nvarchar[*]|  
|nvarchar2[4001..*]|nvarchar(max)|  
|pls_integer|int|  
|RAW [*.. 8000]|varbinary[*]|  
|raw[8001..*]|varbinary(max)|  
|Real|float[53]|  
|ID de ligne|uniqueidentifier|  
|Signtype|smallint|  
|Smallint|smallint|  
|chaîne [*.. 8000]|varchar[*]|  
|string[8001..*]|varchar(max)|  
|TIMESTAMP|datetime2|  
|horodateur avec fuseau horaire local|datetimeoffset|  
|horodateur avec fuseau horaire|datetimeoffset|  
|horodateur avec fuseau horaire local [*.. \*]|datetimeoffset[*]|  
|horodateur avec fuseau horaire [*.. \*]|datetimeoffset[*]|  
|timestamp[*..\*]|datetime2[*]|  
|UROWID|uniqueidentifier|  
|UROWID [*.. \*]|uniqueidentifier|  
|varchar[*..8000]|varchar[*]|  
|varchar[8001..*]|varchar(max)|  
|varchar2[*..8000]|varchar[*]|  
|varchar2[8001..*]|varcha(max)|  
|Xmltype|xml|  
  
## <a name="see-also"></a>Voir aussi  
[Référence de l’Interface utilisateur &#40; OracleToSQL &#41;](../../ssma/oracle/user-interface-reference-oracletosql.md)  
  
