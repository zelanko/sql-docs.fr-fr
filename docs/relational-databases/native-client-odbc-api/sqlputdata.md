---
title: SQLPutData - France Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e063d1053d8a6e5e10a1234d33893adf27fbc3ad
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302340"
---
# <a name="sqlputdata"></a>SQLPutData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les restrictions suivantes s’appliquent lors de l’utilisation de SQLPutData pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] envoyer plus de 65 535 octets de données (pour la version 4.21a) ou 400 KB de données (pour SQL Server version 6.0 et plus tard) pour un SQL_LONGVARCHAR (**texte**), SQL_WLONGVARCHAR (**ntext**) ou SQL_LONGVARBINARY (**image)** colonne:  
  
-   Le paramètre référencé peut être le *insert_value* dans une instruction INSERT.  
  
-   Le paramètre référencé peut être une *expression* dans la clause SET d’une déclaration UPDATE.  
  
 L’annulation d’une séquence d’appels SQLPutData [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui fournissent des données en blocs à un serveur en cours d’exécution provoque une mise à jour partielle de la valeur de la colonne lors de l’utilisation de la version 6.5 ou plus tôt. Le **texte**, **ntext**, ou colonne **d’image** qui a été référencé lorsque SQLCancel a été appelé est réglé à une valeur intermédiaire de placeholder.  
  
> [!NOTE]  
>  Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ne prend pas en charge la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 6.5 ou antérieure.  
  
## <a name="diagnostics"></a>Diagnostics  
 Il y [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a un client autochtone spécifique SQLSTATE pour SQLPutData:  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|22026|Chaîne de données ou longueur non correspondante|Si la longueur des données dans les octets à envoyer a été spécifiée par une application, par exemple, avec SQL_LEN_DATA_AT_EXEC*n*) où *n* est supérieure à 0, le nombre total d’octets donnés par l’application via SQLPutData doit correspondre à la longueur spécifiée.|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>SQLPutData et paramètres table  
 SQLPutData est utilisé par une application lors de l’utilisation de la liaison à ligne variable avec des paramètres de valeur de table. Le paramètre *StrLen_Or_Ind* indique qu’il est prêt pour le conducteur à recueillir des données pour la prochaine rangée ou des rangées de données de paramètres de valeur de table, ou qu’aucune autre ligne n’est disponible :  
  
-   Une valeur supérieure à 0 indique que le jeu suivant de valeurs de ligne est disponible.  
  
-   La valeur 0 indique qu'il ne reste plus de lignes à envoyer.  
  
-   Toute valeur inférieure à 0 est une erreur et entraîne la consignation d'un enregistrement de diagnostic avec SQLState HY090 et le message « Longueur de chaîne ou de mémoire tampon non valide ».  
  
 Le *paramètre DataPtr* est ignoré, mais doit être défini à une valeur non-NULL. Pour plus d’informations, consultez la section sur la fixation variable de la ligne TVP dans [binding et transfert de données des paramètres et des valeurs de colonnes de valeur de table](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Si *StrLen_Or_Ind* a une valeur autre que SQL_DEFAULT_PARAM ou un nombre entre 0 et le SQL_PARAMSET_SIZE (c’est-à-dire le paramètre *ColumnSize* de SQLBindParameter), c’est une erreur. Cette erreur conduit SQLPutData à retourner SQL_ERROR: SQLSTATE=HY090, « Longueur de chaîne ou de mémoire tampon non valide ».  
  
 Pour plus d’informations sur les paramètres de valeur de table, voir [Paramètres de valeur de la table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>Prise en charge de SQLPutData pour les fonctionnalités Date et Heure améliorées  
 Les valeurs de paramètres des types de date/heure sont converties comme décrit dans [Conversions de C à SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).  
  
 Pour plus d’informations, voir [Les améliorations de date et d’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>Prise en charge des grands types définis par l'utilisateur CLR par SQLPutData  
 **SQLPutData** prend en charge les grands types définis par les utilisateurs CLR (UDT). Pour plus d’informations, voir [Grands types définis par l’utilisateur CLR &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLPutData](https://go.microsoft.com/fwlink/?LinkId=59365)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
