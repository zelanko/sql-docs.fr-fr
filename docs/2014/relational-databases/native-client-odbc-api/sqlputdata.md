---
title: SQLPutData | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
author: rothja
ms.author: jroth
ms.openlocfilehash: d847c7df84c1d00ed357a40a72839ff52f5737c1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85021760"
---
# <a name="sqlputdata"></a>SQLPutData
  Les restrictions suivantes s’appliquent lors de l’utilisation de SQLPutData pour envoyer plus de 65 535 octets de données (pour la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 4.21 a) ou de 400 Ko de données (pour SQL Server version 6,0 et ultérieure) pour une colonne SQL_LONGVARCHAR ( `text` ), SQL_WLONGVARCHAR ( `ntext` ) ou SQL_LONGVARBINARY ( `image` ) :  
  
-   Le paramètre référencé peut être le *insert_Value* dans une instruction INSERT.  
  
-   Le paramètre référencé peut être une *expression* dans la clause SET d’une instruction Update.  
  
 L’annulation d’une séquence d’appels SQLPutData qui fournissent des données en blocs à un serveur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provoque une mise à jour partielle de la valeur de la colonne lors de l’utilisation de la version 6,5 ou d’une version antérieure. La `text` `ntext` colonne, ou `image` référencée quand SQLCancel a été appelé est définie sur une valeur d’espace réservé intermédiaire.  
  
> [!NOTE]  
>  Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ne prend pas en charge la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 6.5 ou antérieure.  
  
## <a name="diagnostics"></a>Diagnostics  
 Il existe une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQLSTATE spécifique Native Client pour SQLPutData :  
  
|SQLSTATE|Erreur|Description|  
|--------------|-----------|-----------------|  
|22026|Chaîne de données ou longueur non correspondante|Si la longueur des données en octets à envoyer a été spécifiée par une application, par exemple avec SQL_LEN_DATA_AT_EXEC (*n*) où *n* est supérieur à 0, le nombre total d’octets fournis par l’application via SQLPutData doit correspondre à la longueur spécifiée.|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>SQLPutData et paramètres table  
 SQLPutData est utilisé par une application lors de l’utilisation d’une liaison de ligne variable avec des paramètres table. Le paramètre *StrLen_Or_Ind* indique qu’il est prêt pour le pilote de collecter des données pour la ou les lignes suivantes de données de paramètre table, ou qu’il n’y a plus de lignes disponibles :  
  
-   Une valeur supérieure à 0 indique que le jeu suivant de valeurs de ligne est disponible.  
  
-   La valeur 0 indique qu'il ne reste plus de lignes à envoyer.  
  
-   Toute valeur inférieure à 0 est une erreur et entraîne la consignation d'un enregistrement de diagnostic avec SQLState HY090 et le message « Longueur de chaîne ou de mémoire tampon non valide ».  
  
 Le paramètre *DataPtr* est ignoré, mais doit être défini sur une valeur non null. Pour plus d’informations, consultez la section sur la variable TVP liaison de ligne dans [Binding and transfert de données of Table-valued Parameters and Column Values](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Si *StrLen_Or_Ind* a une valeur autre que SQL_DEFAULT_PARAM ou un nombre compris entre 0 et le SQL_PARAMSET_SIZE (autrement dit, le paramètre de *colonne* de SQLBindParameter), il s’agit d’une erreur. Cette erreur conduit SQLPutData à retourner SQL_ERROR: SQLSTATE=HY090, « Longueur de chaîne ou de mémoire tampon non valide ».  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>Prise en charge de SQLPutData pour les fonctionnalités Date et Heure améliorées  
 Les valeurs de paramètre de types date/heure sont converties comme décrit dans [conversions de C en SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).  
  
 Pour plus d’informations, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>Prise en charge des grands types définis par l'utilisateur CLR par SQLPutData  
 `SQLPutData` prend en charge les grands types CLR définis par l'utilisateur. Pour plus d’informations, consultez [types CLR volumineux définis par l’utilisateur &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLPutData, fonction](https://go.microsoft.com/fwlink/?LinkId=59365)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
