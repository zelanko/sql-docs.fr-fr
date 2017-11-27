---
title: "Paramètres (Type de mappage) du projet (OracleToSQL) | Documents Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bb8466e-2199-4f00-8513-b04e9586723d
caps.latest.revision: "8"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: f387bee9f8e83568bb463ae0e07c4f614a725b15
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
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
  
**Type de cible**  
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
|BFILE|varbinary(max)|  
|BINARY_DOUBLE|float [53]|  
|BINARY_FLOAT|float [53]|  
|binary_integer|int|  
|objet BLOB|varbinary(max)|  
|boolean|bit|  
|char|varchar(max)|  
|char varying|varchar(max)|  
|caractère|varchar(max)|  
|character varying|varchar(max)|  
|CLOB|varchar(max)|  
|date|datetime2 [0]|  
|dec|DEC [38] [0]|  
|decimal|float [53]|  
|double précision|float [53]|  
|float|float [53]|  
|int|int|  
|entier|int|  
|long|varchar(max)|  
|long raw|varbinary(max)|  
|long raw [\*... 8000]<sup>*</sup>|varbinary [*]|  
|long raw [8001..\*]<sup>*</sup>|varbinary(max)|  
|national char|nvarchar(max)|  
|national char varying|nvarchar(max)|  
|caractères nationaux|nvarchar(max)|  
|variable de caractères nationaux<sup>**</sup>|nvarchar(max)|  
|variable de caractères nationaux<sup>*</sup>|nvarchar(max)|  
|nchar|nvarchar(max)|  
|NCLOB|nvarchar(max)|  
|nombre|float [53]|  
|numeric|float [53]|  
|NVARCHAR2|nvarchar(max)|  
|pls_integer|int|  
|brut|varbinary(max)|  
|real|float [53]|  
|ID de ligne|uniqueidentifier|  
|Signtype|smallint|  
|smallint|smallint|  
|chaîne|varchar(max)|  
|timestamp|datetime2|  
|horodateur avec fuseau horaire local|datetimeoffset|  
|horodateur avec fuseau horaire|datetimeoffset|  
|UROWID|uniqueidentifier|  
|varchar|varchar(max)|  
|VARCHAR2|varchar(max)|  
|XmlType|xml|  
  
<sup>*</sup>S’applique pour retourner la valeur type mappage uniquement.  
  
<sup>**</sup>S’applique à l’argument de type mappage uniquement.  
  
### <a name="default-column-type-mapping"></a>Mappage de Type de colonne par défaut  
Le tableau suivant contient le mappage de type par défaut pour les colonnes.  
  
|Type de données Oracle|Par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Type de données|  
|--------------------|-------------------------------------------------------------------------|  
|BFILE|varbinary(max)|  
|BINARY_DOUBLE|float [53]|  
|BINARY_FLOAT|float [53]|  
|objet BLOB|varbinary(max)|  
|char|char|  
|char varying [*.. \*]|varchar [*]|  
|Char [*.. \*]|Char [*]|  
|caractère|char|  
|variable de caractères [*.. \*]|varchar [*]|  
|caractère [*.. \*]|Char [*]|  
|CLOB|varchar(max)|  
|date|datetime2 [0]|  
|dec|DEC [38] [0]|  
|DEC [*.. \*]|DEC [*] [0]|  
|DEC [*.. \*][\*.. \*]|dec[*][\*]|  
|decimal|Decimal [38] [0]|  
|Decimal [*.. \*]|Decimal [*] [0]|  
|Decimal [*.. \*][\*.. \*]|Decimal [*] [\*]|  
|double précision|float [53]|  
|float|float [53]|  
|float [*.. 53]|float [*]|  
|float [54.. *]|float [53]|  
|int|int|  
|entier|int|  
|long|varchar(max)|  
|long raw|varbinary(max)|  
|long raw [*.. 8000]|varbinary [*]|  
|long raw [8001.. *]|varbinary(max)|  
|long varchar|varchar(max)|  
|long [*.. 8000]|varchar [*]|  
|long [8001.. *]|varchar(max)|  
|national char|nchar|  
|national char varying [*.. \*]|nvarchar [*]|  
|national char [*.. \*]|NCHAR [*]|  
|caractères nationaux|nchar|  
|variable de caractères nationaux [*.. \*]|nvarchar [*]|  
|les caractères nationaux [*.. \*]|NCHAR [*]|  
|nchar|nchar|  
|NCHAR [*]|NCHAR [*]|  
|NCLOB|nvarchar(max)|  
|nombre|float [53]|  
|nombre [*.. \*]|numérique [*]|  
|nombre [*.. \*][\*.. \*]|numérique [*] [\*]|  
|numeric|numeric|  
|numérique [*.. \*]|numérique [*]|  
|numérique [*.. \*][\*.. \*]|numérique [*] [\*]|  
|NVARCHAR2 [*.. \*]|nvarchar [*]|  
|RAW [*.. \*]|varbinary [*]|  
|real|float [53]|  
|ID de ligne|uniqueidentifier|  
|smallint|smallint|  
|timestamp|datetime2|  
|horodateur avec fuseau horaire local|datetimeoffset|  
|horodateur avec fuseau horaire local [*.. \*]|DateTimeOffset [*]|  
|horodateur avec fuseau horaire|datetimeoffset|  
|horodateur avec fuseau horaire [*.. \*]|DateTimeOffset [*]|  
|timestamp [*.. \*]|datetime2 [*]|  
|UROWID|uniqueidentifier|  
|UROWID [*.. \*]|uniqueidentifier|  
|varchar [*.. \*]|varchar [*]|  
|VARCHAR2 [*.. \*]|varchar [*]|  
|XmlType|xml|  
  
### <a name="default-local-variable-type-mapping"></a>Mappage de Type de Variable locale par défaut  
Le tableau suivant contient le mappage de type par défaut pour les variables locales.  
  
|Type de données Oracle|Par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Type de données|  
|--------------------|-------------------------------------------------------------------------|  
|BFILE|varbinary(max)|  
|BINARY_DOUBLE|float [53]|  
|BINARY_FLOAT|float [53]|  
|binary_interger|int|  
|Objet BLOB|varbinary(max)|  
|Booléen|bit|  
|Char|char|  
|char varying [*.. 8000]|varchar [*]|  
|char varying [8001.. *]|varchar(max)|  
|Char [*.. 8000]|Char [*]|  
|Char [8001.. *]|varchar(max)|  
|Caractère|char|  
|variable de caractères [*.. 8000]|varchar [*]|  
|variable de caractères [8001.. *]|varchar(max)|  
|caractère [*.. 8000]|Char [*]|  
|caractère [8001.. *]|varchar(max)|  
|CLOB|varchar(max)|  
|date|datetime2 [0]|  
|dec|DEC [38] [0]|  
|DEC [*.. \*]|DEC [*] [0]|  
|DEC [*.. \*][\*.. \*]|dec[*][\*]|  
|decimal|Decimal [38] [0]|  
|Decimal [*.. \*]|Decimal [*] [0]|  
|Decimal [*.. \*][\*.. \*]|Decimal [*] [\*]|  
|double précision|float [53]|  
|Float|float [53]|  
|float [*.. 53]|float [*]|  
|float [54.. *]|float [53]|  
|int|int|  
|Entier|int|  
|entier [*.. \*]|numérique [*] [0]|  
|Long|varchar(max)|  
|long raw|varbinary(max)|  
|long raw [*.. 8000]|varbinary [*]|  
|long raw [8001.. *]|varbinary(max)|  
|national char|nchar|  
|national char varying [*.. 4000]|nvarchar [*]|  
|national char varying [4001.. *]|nvarchar(max)|  
|national char [*.. 4000]|NCHAR [*]|  
|national char [4001.. *]|nvarchar(max)|  
|caractères nationaux|nchar|  
|les caractères nationaux [*.. 4000]|nvarchar [*]|  
|les caractères nationaux [4001.. *]|nvarchar(max)|  
|variable de caractères nationaux [*.. 4000]|nvarchar [*]|  
|variable de caractères nationaux [4001.. *]|nvarchar(max)|  
|Nchar|nchar|  
|NCHAR [*.. 4000]|NCHAR [*]|  
|NCHAR [4001.. *]|nvarchar(max)|  
|NCHAR varying [*.. 4000]|nvarchar [*]|  
|NCHAR varying [4001.. *]|nvarchar(max)|  
|NCLOB|nvarchar(max)|  
|Number|float [53]|  
|nombre [*.. \*]|numérique [*]|  
|nombre [*.. \*][\*.. \*]|numérique [*] [\*]|  
|Numérique|numérique [38] [0]|  
|numérique [*.. \*]|numérique [*]|  
|numérique [*.. \*][\*.. \*]|numérique [*] [\*]|  
|NVARCHAR2 [*.. 4000]|nvarchar [*]|  
|NVARCHAR2 [4001.. *]|nvarchar(max)|  
|pls_integer|int|  
|RAW [*.. 8000]|varbinary [*]|  
|RAW [8001.. *]|varbinary(max)|  
|Real|float [53]|  
|ID de ligne|uniqueidentifier|  
|Signtype|smallint|  
|Smallint|smallint|  
|chaîne [*.. 8000]|varchar [*]|  
|chaîne [8001.. *]|varchar(max)|  
|timestamp|datetime2|  
|horodateur avec fuseau horaire local|datetimeoffset|  
|horodateur avec fuseau horaire|datetimeoffset|  
|horodateur avec fuseau horaire local [*.. \*]|DateTimeOffset [*]|  
|horodateur avec fuseau horaire [*.. \*]|DateTimeOffset [*]|  
|timestamp [*.. \*]|datetime2 [*]|  
|UROWID|uniqueidentifier|  
|UROWID [*.. \*]|uniqueidentifier|  
|varchar [*.. 8000]|varchar [*]|  
|varchar [8001.. *]|varchar(max)|  
|VARCHAR2 [*.. 8000]|varchar [*]|  
|VARCHAR2 [8001.. *]|varcha(max)|  
|XmlType|xml|  
  
## <a name="see-also"></a>Voir aussi  
[Référence de l’Interface utilisateur &#40; OracleToSQL &#41;](../../ssma/oracle/user-interface-reference-oracletosql.md)  
  
