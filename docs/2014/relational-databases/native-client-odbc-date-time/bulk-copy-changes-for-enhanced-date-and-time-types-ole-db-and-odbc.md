---
title: Modifications de copie en bloc pour les types de date et d’heure améliorés (OLE DB et ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, bulk copy operations
- bulk copy [ODBC], changes for date/time improvements
ms.assetid: c29e0f5e-9b3c-42b3-9856-755f4510832f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 855d0baf0b0b890b9343378f8060919979d5f206
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63207104"
---
# <a name="bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc"></a>Modifications de la copie en bloc pour les types date/heure améliorés (OLE DB et ODBC)
  Cette rubrique décrit les améliorations de date/heure permettant de prendre en charge les fonctionnalités de copie en bloc. Les informations fournies dans cette rubrique sont valables pour OLE DB et ODBC dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="format-files"></a>Fichiers de format  
 Lors de la génération interactive de fichiers de format, le tableau ci-dessous décrit l'entrée utilisée pour spécifier des types date/heure et les noms de type de données de fichier hôte correspondants.  
  
|type de stockage de fichier|Type de données du fichier hôte|Réponse à l’invite : « Entrez le type de stockage de fichier du champ <nom_champ> [\<valeur_par_défaut>] : »|  
|-----------------------|-------------------------|-----------------------------------------------------------------------------------------------------|  
|Datetime|SQLDATETIME|d|  
|Smalldatetime|SQLDATETIM4|D|  
|Date|SQLDATE|de|  
|Heure|SQLTIME|te|  
|Datetime2|SQLDATETIME2|d2|  
|Datetimeoffset|SQLDATETIMEOFFSET|do|  
  
 Le fichier au format XML XSD possédera les ajouts suivants :  
  
```  
<xs:complexType name="SQLDATETIME2">  
    <xs:complexContent>  
        <xs:extension base="bl:Fixed"/>  
    </xs:complexContent>  
</xs:complexType>  
<xs:complexType name="SQLDATETIMEOFFSET">  
    <xs:complexContent>  
        <xs:extension base="bl:Fixed"/>  
    </xs:complexContent>  
</xs:complexType>  
<xs:complexType name="SQLDATE">  
    <xs:complexContent>  
        <xs:extension base="bl:Fixed"/>  
    </xs:complexContent>  
</xs:complexType>  
<xs:complexType name="SQLTIME">  
    <xs:complexContent>  
        <xs:extension base="bl:Fixed"/>  
    </xs:complexContent>  
</xs:complexType>  
```  
  
## <a name="character-data-files"></a>Fichiers de données de type caractère  
 Dans les fichiers de données de type caractère, les valeurs de date et d’heure sont représentées comme décrit dans la section « formats de données : chaînes et littéraux » de [type de données pour les améliorations de date et d’heure ODBC](data-type-support-for-odbc-date-and-time-improvements.md) pour ODBC, ou [pour la prise en charge de type de données pour OLE DB améliorations de la date et](../native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md) de l’heure pour les OLE DB.  
  
 Dans les natifs de données natives, les valeurs de date et d’heure pour les quatre nouveaux types sont représentées comme leurs représentations TDS avec une échelle de 7 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (car il s’agit de la valeur maximale prise en charge par et les fichiers de données BCP ne stockent pas l’échelle de ces colonnes). Aucune modification n’est apportée au stockage des `datetime` représentations `smalldatetime` existing et existing ou de leurs Tabular Data Stream (TDS).  
  
 Les tailles de stockage pour les différents types de stockage sont les suivantes pour OLE DB :  
  
|type de stockage de fichier|Taille de stockage en octets|  
|-----------------------|---------------------------|  
|DATETIME|8|  
|smalldatetime|4|  
|Date|3|  
|time|6|  
|datetime2|9|  
|datetimeoffset|11|  
  
 Les tailles sont les suivantes pour ODBC. Notez qu'il n'est pas nécessaire de stocker la précision dans les fichiers de format ou de données, car BCP.exe extraira toujours la précision du serveur.  
  
|type de stockage de fichier|Taille de stockage en octets|Format de stockage|  
|-----------------------|---------------------------|--------------------|  
|datetime (d)|8|TDS (flux de données tabulaires)|  
|smalldatetime (D)|4|TDS (flux de données tabulaires)|  
|date (de)|3|TDS (flux de données tabulaires)|  
|time (te)|6|TDS (flux de données tabulaires)|  
|datetime2 (d2)|9|TDS (flux de données tabulaires)|  
|datetimeoffset (do)|11|TDS (flux de données tabulaires)|  
  
## <a name="bcp-types-in-sqlnclih"></a>Types BCP dans sqlncli.h  
 Les types suivants sont définis dans sqlncli.h pour être utilisés avec les extensions d'API BCP d'ODBC. Ces types sont passés avec le paramètre *eUserDataType* de IBCPSession::BCPColFmt dans OLE DB.  
  
|type de stockage de fichier|Type de données du fichier hôte|Tapez sqlncli. h pour l’utiliser avec IBCPSession :: BCPColFmt|Value|  
|-----------------------|-------------------------|-----------------------------------------------------------|-----------|  
|Datetime|SQLDATETIME|BCP_TYPE_SQLDATETIME|0x3d|  
|Smalldatetime|SQLDATETIM4|BCP_TYPE_SQLDATETIME4|0x3a|  
|Date|SQLDATE|BCP_TYPE_SQLDATE|0x28|  
|Heure|SQLTIME|BCP_TYPE_SQLTIME|0x29|  
|Datetime2|SQLDATETIME2|BCP_TYPE_SQLDATETIME2|0x2a|  
|Datetimeoffset|SQLDATETIMEOFFSET|BCP_TYPE_SQLDATETIMEOFFSET|0x2b|  
  
## <a name="bcp-data-type-conversions"></a>Conversions des types de données BCP  
 Les tableaux ci-dessous fournissent des informations de conversion.  
  
 **Remarque pour OLE DB** : Les conversions suivantes sont effectuées par IBCPSession. IRowsetFastLoad utilise des conversions OLE DB telles que définies dans [Conversions effectuées de client à serveur](../native-client-ole-db-date-time/conversions-performed-from-client-to-server.md). Notez que les valeurs datetime sont arrondies au 1/300e de seconde et que les secondes des valeurs smalldatetime sont mises à zéro après l'exécution des conversions clientes décrites ci-dessous. L'arrondi des valeurs datetime est propagé aux heures et aux minutes, mais pas à la date.  
  
|À --><br /><br /> À partir|Date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|char|wchar|  
|------------------------|----------|----------|-------------------|--------------|---------------|--------------------|----------|-----------|  
|Date|1|-|1,6|1,6|1,6|1,5,6|1,3|1,3|  
|Heure|NON APPLICABLE|1,10|1,7,10|1,7,10|1,7,10|1,5,7,10|1,3|1,3|  
|Smalldatetime|1,2|1,4,10|1|1|1,10|1,5,10|1,11|1,11|  
|Datetime|1,2|1,4,10|1,12|1|1,10|1,5,10|1,11|1,11|  
|Datetime2|1,2|1,4,10|1,10 (ODBC)1,12 (OLE DB)|1,10|1,10|1,5,10|1,3|1,3|  
|Datetimeoffset|1,2,8|1,4,8,10|1,8,10|1,8,10|1,8,10|1,10|1,3|1,3|  
|Char/wchar (date)|9|-|9,6 (ODBC)9,6,12 (OLE DB)|9,6 (ODBC)9,6,12 (OLE DB)|9,6|9,5,6|NON APPLICABLE|NON APPLICABLE|  
|Char/wchar (heure)|-|9,10|9,7,10 (ODBC)9,7,10,12 (OLE DB)|9,7,10 (ODBC)9,7,10, 12 (OLE DB)|9,7,10|9,5,7,10|NON APPLICABLE|NON APPLICABLE|  
|Char/wchar (datetime)|9,2|9,4,10|9,10 (ODBC)9,10,12 (OLE DB)|9,10 (ODBC)9,10,12 (OLE DB)|9,10|9,5,10|NON APPLICABLE|NON APPLICABLE|  
|Char/wchar (datetimeoffset)|9,2,8|9,4,8,10|9,8,10 (ODBC)9,8,10,12 (OLE DB)|9,8,10 (ODBC)9,8,10,12 (OLE DB)|9,8,10|9,10|NON APPLICABLE|NON APPLICABLE|  
  
#### <a name="key-to-symbols"></a>Liste des symboles  
  
|Symbole|Signification|  
|------------|-------------|  
|-|Aucune conversion n'est prise en charge.<br /><br /> Un enregistrement de diagnostic ODBC est généré avec SQLSTATE 07006 et le message « Violation de l'attribut de type de données restreint ».|  
|1|Si les données fournies ne sont pas valides, un enregistrement de diagnostic ODBC est généré avec SQLSTATE 22007 et le message « Format datetime non valide ». Pour les valeurs datetimeoffset, la partie heure doit se situer dans la plage après la conversion au format UTC, même si aucune conversion au format UTC n'est demandée. Ceci tient au fait que TDS et le serveur normalisent toujours l'heure dans les valeurs datetimeoffset pour UTC. Par conséquent, le client doit vérifier que les composants heure se situent dans la plage prise en charge après la conversion au format UTC.|  
|2|Le composant heure est ignoré.|  
|3|Pour ODBC, si la troncation avec perte de données se produit, un enregistrement de diagnostic est généré avec SQLSTATE 22001 et le message « chaîne de données, tronqué à droite » le nombre de chiffres de fraction de seconde (l’échelle) est déterminé à partir de la taille de la colonne de destination, conformément au tableau suivant. Pour les tailles de colonne supérieures à la plage du tableau, une échelle de 7 est nécessaire. Cette conversion accepte jusqu'à neuf chiffres de fractions de seconde, valeur maximale autorisée par ODBC.<br /><br /> **Tapez :** DBTIME2<br /><br /> **Échelle impliquée 0**8<br /><br /> **Échelle impliquée 1.. 7** 10, 16<br /><br /> <br /><br /> **Tapez :** DBTIMESTAMP<br /><br /> **Échelle impliquée 0 :** 19<br /><br /> **Échelle impliquée 1.. 7 :** 21.. 27<br /><br /> <br /><br /> **Type :** DBTIMESTAMPOFFSET<br /><br /> **Échelle impliquée 0 :** 26<br /><br /> **Échelle impliquée 1.. 7 :** 28.. 34<br /><br /> Pour OLE DB, s'il se produit une troncation avec perte de données, une erreur est publiée. Pour datetime2, le nombre de chiffres des fractions de seconde (l'échelle) est déterminé à partir de la taille de la colonne de destination, conformément au tableau suivant. pour les tailles de colonne supérieures à la plage du tableau, une échelle de 9 est nécessaire. Cette conversion accepte jusqu'à neuf chiffres de fractions de seconde, valeur maximale autorisée par OLE DB.<br /><br /> **Tapez :** DBTIME2<br /><br /> **Échelle impliquée 0**8<br /><br /> **Échelle impliquée 1..9** 1..9<br /><br /> <br /><br /> **Tapez :** DBTIMESTAMP<br /><br /> **Échelle impliquée 0 :** 19<br /><br /> **Échelle impliquée 1..9 :** 21..29<br /><br /> <br /><br /> **Type :** DBTIMESTAMPOFFSET<br /><br /> **Échelle impliquée 0 :** 26<br /><br /> **Échelle impliquée 1..9 :** 28..36|  
|4|Le composant date est ignoré.|  
|5|Le composant fuseau horaire est défini au format UTC (par exemple, 00:00).|  
|6|L'heure est définie avec la valeur zéro.|  
|7|La date est définie avec la valeur 1900-01-01.|  
|8|Le décalage horaire est ignoré.|  
|9|La chaîne est analysée et convertie en valeur date, datetime, datetimeoffset ou time, selon le premier caractère de ponctuation rencontré et la présence de composants restants. La chaîne est ensuite convertie en type cible, selon les règles fournies dans le tableau à la fin de cette rubrique pour le type source découvert par ce processus. Si les données fournies ne peuvent pas être analysées sans erreur, ou si un composant quelconque est en dehors de la plage autorisée, ou s'il n'y a aucune conversion du type de littéral au type cible, une erreur est publiée (OLE DB) ou un enregistrement de diagnostic ODBC est généré avec SQLSTATE 22018 et le message « Valeur de caractère non valide pour la spécification de la casse ». Pour les paramètres datetime et smalldatetime, si l'année est en dehors de la plage prise en charge par ces types, une erreur est publiée (OLE DB) ou un enregistrement de diagnostic ODBC est généré avec SQLSTATE 22007 et le message « Format datetime non valide ».<br /><br /> Pour datetimeoffset, la valeur doit se situer dans la plage après la conversion au format UTC, même si aucune conversion au format UTC n'est demandée. Cela tient au fait que TDS et le serveur normalisent toujours l'heure des valeurs datetimeoffset pour UTC, si bien que le client doit vérifier que les composants heure se situent dans la plage prise en charge après la conversion au format UTC. Si la valeur n'est pas dans la plage UTC prise en charge, une erreur est publiée (OLE DB) ou un enregistrement de diagnostic ODBC est généré avec SQLSTATE 22007 et le message « Format datetime non valide ».|  
|10|S'il se produit une troncation avec perte de données lors d'une conversion de client à serveur, une erreur est publiée (OLE DB) ou un enregistrement de diagnostic ODBC est généré avec SQLSTATE 22008 et le message « Dépassement de la capacité du champ datetime ». Cette erreur se produit également si la valeur est située en dehors de la plage qui peut être représentée par la plage UTC utilisée par le serveur. S'il se produit une troncation de secondes ou de fractions de seconde lors d'une conversion de serveur à client, seul un avertissement est émis.|  
|11|S'il se produit une troncation avec perte de données, un enregistrement de diagnostic est généré.<br /><br /> Lors d'une conversion de serveur à client, il s'agit d'un avertissement (ODBC SQLSTATE S1000).<br /><br /> Lors d'une conversion de client à serveur, il s'agit d'une erreur (ODBC SQLSTATE 22001).|  
|12|Les secondes sont réinitialisées et les fractions de seconde sont ignorées. Aucune erreur de troncation n'est possible.|  
|NON APPLICABLE|Le comportement existant et antérieur de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] est conservé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorations de la date et de l’heure &#40;ODBC&#41;](date-and-time-improvements-odbc.md)   
 [Améliorations des types de données de date et d’heure &#40;OLE DB&#41;](../native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
