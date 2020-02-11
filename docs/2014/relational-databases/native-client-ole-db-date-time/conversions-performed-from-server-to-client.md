---
title: Conversions effectuées du serveur au client | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB], server to client
ms.assetid: 676fdf24-fb72-4ea0-a8d2-2b197da3c83f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d9e922f5bf8d07e75c976dbfc07b89b8527dbbc8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63023373"
---
# <a name="conversions-performed-from-server-to-client"></a>Conversions de serveur à client
  Cette rubrique décrit les conversions date/heure effectuées entre [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou version ultérieure) et une application cliente écrite avec OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="conversions"></a>Conversions  
 Le tableau suivant décrit les conversions entre le type retourné au client et le type de la liaison. Pour les paramètres de sortie, si ICommandWithParameters :: SetParameterInfo a été appelé et que le type spécifié dans *pwszDataSourceType* ne correspond pas au type réel sur le serveur, une conversion implicite est effectuée par le serveur, et le type retourné au client correspond au type spécifié par le biais de ICommandWithParameters :: SetParameterInfo. Cela peut entraîner des résultats de conversion inattendus lorsque les règles de conversion du serveur sont différentes de celles décrites dans cette rubrique. Par exemple, quand une date par défaut doit être fournie, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise 1900-1-1, plutôt que 1899-12-30.  
  
|><br /><br /> De|DATE|DBDATE|DBTIME|DBTIME2|DBTIMESTAMP|DBTIMESTAMPOFFSET|FILETIME|BYTES|VARIANT|SSVARIANT|BSTR|STR|WSTR|  
|----------------------|----------|------------|------------|-------------|-----------------|-----------------------|--------------|-----------|-------------|---------------|----------|---------|----------|  
|Date|1,7|OK|-|-|1|1,3|1,7|-|OK (VT_BSTR)|OK|OK|4|4|  
|Temps|5, 6, 7|-|9|OK|6|3, 6|5, 6|-|OK (VT_BSTR)|OK|OK|4|4|  
|Smalldatetime|7|8|9,10|10|OK|3|7|-|7 (VT_DATE)|OK|OK|4|4|  
|Datetime|5, 7|8|9,10|10|OK|3|7|-|7 (VT_DATE)|OK|OK|4|4|  
|Datetime2|5, 7|8|9,10|10|7|3|5, 7|-|OK (VT_BSTR)|OK|OK|4|4|  
|Datetimeoffset|5, 7, 11|8, 11|9, 10, 11|10, 11|7, 11|OK|5, 7, 11|-|OK (VT_BSTR)|OK|OK|4|4|  
|Char, Varchar,<br /><br /> NVARCHAR2, NCHAR|7, 13|12|12, 9|12|12|12|7, 13|N/A|N/A|N/A|N/A|N/A|N/A|  
|Sql_variant<br /><br /> (datetime)|7|8|9,10|10|OK|3|7|-|7(VT_DATE)|OK|OK|4|4|  
|Sql_variant<br /><br /> (smalldatetime)|7|8|9,10|10|OK|3|7|-|7(VT_DATE)|OK|OK|4|4|  
|Sql_variant<br /><br /> (date)|1,7|OK|2|2|1|1,3|1,7|-|OK(VT_BSTR)|OK|OK|4|4|  
|Sql_variant<br /><br /> (time)|5, 6, 7|2|6|OK|6|3, 6|5, 6|-|OK(VT_BSTR)|OK|OK|4|4|  
|Sql_variant<br /><br /> (datetime2)|5, 7|8|9,10|10|OK|3|5, 7|-|OK(VT_BSTR)|OK|OK|4|4|  
|Sql_variant<br /><br /> (datetimeoffset)|5, 7, 11|8, 11|9, 10, 11|10, 11|7, 11|OK|5, 7, 11|-|OK(VT_BSTR)|OK|OK|4|4|  
  
## <a name="key-to-symbols"></a>Liste des symboles  
  
|Symbole|Signification|  
|------------|-------------|  
|OK|Aucune conversion nécessaire.|  
|-|Aucune conversion n'est prise en charge. Si la liaison est validée quand IAccessor :: CreateAccessor est appelé, DBBINDSTATUS_UPSUPPORTEDCONVERSION est retourné dans *rgStatus*. Lorsque la validation pour l'accesseur est différée, DBSTATUS_E_BADACCESSOR est défini.|  
|1|Les champs heure sont définis avec la valeur zéro.|  
|2|DBSTATUS_E_CANTCONVERTVALUE est défini.|  
|3|Le décalage est défini avec la valeur zéro.|  
|4|Si la mémoire tampon du client n'est pas assez grande, DBSTATUS_S_TRUNCATED est défini. Lorsque le type de serveur inclut des fractions de seconde, le nombre de chiffres de la chaîne de résultats correspond exactement à l'échelle du type de serveur.|  
|5|La troncation de secondes ou de fractions de seconde est ignorée.|  
|6|La date est définie avec la date courante, à moins que la source ne soit un littéral de chaîne heure et que la destination soit DBTYPE_DATE. Dans ce cas, c'est 1899-12-30 qui est utilisé.|  
|7|En cas de dépassement de capacité de la valeur, DBSTATUS_E_DATAOVERFLOW est défini.|  
|8|Les champs time (heure) sont ignorés.|  
|9|Les champs de fractions de seconde sont ignorés.|  
|10|Le composant date est ignoré.|  
|11|L'heure est convertie en fuseau horaire du client. Si une erreur se produit pendant cette conversion, DBSTATUS_E_DATAOVERFLOW est défini.|  
|12|La chaîne est analysée comme littéral ISO et convertie dans le type cible. En cas d'échec, la chaîne est analysée comme littéral de date OLE (qui possède aussi des composants heure) et convertie d'une date OLE (DBTYPE_DATE) en type cible. La chaîne doit se conformer à la syntaxe des littéraux autorisés du type cible pour que l'analyse du format ISO réussisse. Pour que l'analyse OLE réussisse, la chaîne doit se conformer à la syntaxe reconnue par OLE. Si la chaîne ne peut pas être analysée, DBSTATUS_E_CANTCONVERTVALUE est défini. Si les valeurs d'un composant sont hors limites, DBSTATUS_E_DATAOVERFLOW est défini.|  
|13|La chaîne est analysée comme littéral ISO et convertie dans le type cible. En cas d'échec, la chaîne est analysée comme littéral de date OLE (qui possède aussi des composants heure) et convertie d'une date OLE (DBTYPE_DATE) en type cible. La chaîne doit se conformer à la syntaxe des littéraux datetime, à moins que la destination ne soit DBTYPE_DATE ou DBTYPE_DBTIMESTAMP. Si tel est le cas, un littéral datetime ou time est autorisé pour que l'analyse de format ISO réussisse. Pour que l'analyse OLE réussisse, la chaîne doit se conformer à la syntaxe reconnue par OLE. Si la chaîne ne peut pas être analysée, DBSTATUS_E_CANTCONVERTVALUE est défini. Si les valeurs d'un composant sont hors limites, DBSTATUS_E_DATAOVERFLOW est défini.|  
  
## <a name="see-also"></a>Voir aussi  
 [Liaisons et conversions &#40;OLE DB&#41;](conversions-ole-db.md)  
  
  
