---
title: UDT volumineux
description: Montre comment récupérer des données à partir des UDT de valeur élevée introduits dans SQL Server 2008.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 06abbc88d80dffba14a48d82561dd4db1a2eb68e
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924329"
---
# <a name="large-udts"></a>UDT volumineux

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Les types définis par l’utilisateur (UDT) permettent au développeur d’étendre le système de type scalaire du serveur en stockant des objets CLR (Common Language Runtime) dans une base de données SQL Server. Les UDT peuvent contenir plusieurs éléments et avoir des comportements, contrairement aux types de données alias traditionnels, qui ne comprennent qu’un seul type de données système SQL Server.  
  
Auparavant, les UDT étaient limités à une taille maximale de 8 kilo-octets. Dans SQL Server 2008, cette restriction a été supprimée pour les UDT ayant un format <xref:Microsoft.Data.SqlClient.Server.Format.UserDefined>.  
  
Pour obtenir la documentation complète sur les types définis par l’utilisateur, consultez [Types CLR définis par l’utilisateur](https://go.microsoft.com/fwlink/?LinkId=98366) à partir de la Documentation en ligne de SQL Server.
  
## <a name="retrieving-udt-schemas-using-getschema"></a>Récupération de schémas UDT à l’aide de GetSchema  
La méthode <xref:Microsoft.Data.SqlClient.SqlConnection.GetSchema%2A> de <xref:Microsoft.Data.SqlClient.SqlConnection> retourne les informations de schéma de base de données dans une <xref:System.Data.DataTable>.
  
### <a name="getschematable-column-values-for-udts"></a>Valeurs de colonne GetSchemaTable pour les UDT  
La méthode <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> d’un <xref:Microsoft.Data.SqlClient.SqlDataReader> retourne une <xref:System.Data.DataTable> qui décrit les métadonnées de la colonne. La table suivante décrit les différences dans les métadonnées de colonne pour les UDT volumineux entre SQL Server 2005 et SQL Server 2008.  
  
|Colonne SqlDataReader|SQL Server 2005|SQL Server 2008 et ultérieur|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Variable|Variable|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|Instance UDT|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|Instance UDT|  
|`ProviderType`|21 (`SqlDbType.VarBinary`)|29 (`SqlDbType.Udt`)|  
|`NonVersionedProviderType`|29 (`SqlDbType.Udt`)|29 (`SqlDbType.Udt`)|  
|`DataTypeName`|`SqlDbType.VarBinary`|Nom en trois parties spécifié sous la forme *Database.SchemaName.TypeName*.|  
|`IsLong`|Variable|Variable|  
  
## <a name="sqldatareader-considerations"></a>Considérations relatives à SqlDataReader  
L’objet <xref:Microsoft.Data.SqlClient.SqlDataReader> a été étendu à compter de SQL Server 2008 pour prendre en charge la récupération des valeurs UDT volumineuses. La façon dont les valeurs UDT volumineuses sont traitées par un <xref:Microsoft.Data.SqlClient.SqlDataReader> dépend de la version de SQL Server que vous utilisez, ainsi que de la `Type System Version` spécifiée dans la chaîne de connexion. Pour plus d’informations, consultez <xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
Les méthodes suivantes de <xref:Microsoft.Data.SqlClient.SqlDataReader> retournent un <xref:System.Data.SqlTypes.SqlBinary> au lieu d’un type défini par l’utilisateur (UDT) lorsque la `Type System Version` est définie sur SQL Server 2005 :  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
Les méthodes suivantes retournent un tableau de `Byte[]` au lieu d’un type défini par l’utilisateur (UDT) lorsque la `Type System Version` est définie sur SQL Server 2005 :  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
Notez qu’aucune conversion n’est effectuée pour la version actuelle de ADO.NET.  
  
## <a name="specifying-sqlparameters"></a>Spécification de SqlParameters  
Les propriétés suivantes de <xref:Microsoft.Data.SqlClient.SqlParameter> ont été étendues pour fonctionner avec des UDT volumineux.  
  
|Propriété SqlParameter|Description|  
|---------------------------|-----------------|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Value%2A>|Obtient ou définit un objet représentant la valeur du paramètre. La valeur par défaut est null. La propriété peut être `SqlBinary`, `Byte[]` ou un objet managé.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.SqlValue%2A>|Obtient ou définit un objet représentant la valeur du paramètre. La valeur par défaut est null. La propriété peut être `SqlBinary`, `Byte[]` ou un objet managé.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Size%2A>|Obtient ou définit la taille de la valeur du paramètre à résoudre. La valeur par défaut est 0. La propriété peut être un entier qui représente la taille de la valeur du paramètre. Pour les UDT volumineux, elle peut être la taille réelle de l’UDT, ou -1 pour inconnu.|  
  
## <a name="retrieving-data-example"></a>Exemple de récupération de données  
Le fragment de code suivant montre comment récupérer des donnée UDT volumineuses. La variable `connectionString` suppose une connexion valide à une base de données SQL Server et la variable `commandString` suppose une instruction SELECT valide avec la colonne de clé primaire qui est indiquée en premier.  
  
```csharp  
using (SqlConnection connection = new SqlConnection(   
    connectionString, commandString))  
{  
  connection.Open();  
  SqlCommand command = new SqlCommand(commandString);  
  SqlDataReader reader = command.ExecuteReader();  
  while (reader.Read())  
  {  
    // Retrieve the value of the Primary Key column.  
    int id = reader.GetInt32(0);  
  
    // Retrieve the value of the UDT.  
    LargeUDT udt = (LargeUDT)reader[1];  
  
    // You can also use GetSqlValue and GetValue.  
    // LargeUDT udt = (LargeUDT)reader.GetSqlValue(1);  
    // LargeUDT udt = (LargeUDT)reader.GetValue(1);  
  
    Console.WriteLine(  
     "ID={0} LargeUDT={1}", id, udt);  
  }  
reader.close  
}  
```  
  
## <a name="next-steps"></a>Étapes suivantes
- [Données binaires et à valeurs élevées SQL Server](sql-server-binary-large-value-data.md)
 