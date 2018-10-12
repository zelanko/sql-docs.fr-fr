---
title: Récupérer des types date et heure sous forme de chaînes avec le pilote SQLSRV | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date and time types, retrieving as strings
ms.assetid: 58a974ea-4daf-4e3b-98ed-9731b9c9250f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 29e36f2246556da7a43c3b8335f7a4e3479ae63c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47686987"
---
# <a name="how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver"></a>Procédure : récupérer des types de date et heure sous forme de chaînes à l’aide du pilote SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette fonctionnalité a été ajoutée dans la version 1.1 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] et elle est uniquement valide quand vous utilisez le pilote SQLSRV pour [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. C’est une erreur d’utiliser l’option de connexion ReturnDatesAsStrings avec le pilote PDO_SQLSRV.  
  
Vous pouvez récupérer des types de date et d’heure (**datetime**, **date**, **time**, **datetime2** et **datetimeoffset**) sous forme de chaînes en spécifiant une option dans la chaîne de connexion.  
  
### <a name="to-retrieve-date-and-time-types-as-strings"></a>Pour récupérer des types de date et heure sous forme de chaînes  
  
-   Utilisez l’option de connexion suivante :  
  
    ```  
    'ReturnDatesAsStrings'=>true  
    ```  
  
    La valeur par défaut est **false**, ce qui signifie que les types **datetime**, **Date**, **Time**, **DateTime2**et **DateTimeOffset** sont retournés en tant que types **Datetime** PHP.  
  
## <a name="example"></a> Exemple  
L’exemple suivant montre la syntaxe permettant de récupérer des types de date et heure sous forme de chaînes.  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", 'ReturnDatesAsStrings '=> true);  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a> Exemple  
L’exemple suivant montre que vous pouvez récupérer des dates sous forme de chaînes en spécifiant UTF-8 lors de la récupération de la chaîne, même quand la connexion a été établie avec `"ReturnDatesAsStrings" => false`.  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", "ReturnDatesAsStrings" => false);  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "SELECT VersionDate FROM AWBuildVersion";  
  
$stmt = sqlsrv_query( $conn, $tsql);  
  
if ( $stmt === false ) {  
   echo "Error in statement preparation/execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_fetch( $stmt );  
  
// retrieve date as string  
$date = sqlsrv_get_field( $stmt, 0, SQLSRV_PHPTYPE_STRING("UTF-8"));  
  
if( $date === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
echo $date;  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a> Exemple  
L’exemple suivant montre comment récupérer des dates sous forme de chaînes en spécifiant UTF-8 et `"ReturnDatesAsStrings" => true` dans la chaîne de connexion.  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", 'ReturnDatesAsStrings'=> true, "CharacterSet" => 'utf-8' );  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "SELECT VersionDate FROM AWBuildVersion";  
  
$stmt = sqlsrv_query( $conn, $tsql);  
  
if ( $stmt === false ) {  
   echo "Error in statement preparation/execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_fetch( $stmt );  
  
// retrieve date as string  
$date = sqlsrv_get_field( $stmt, 0 );  
  
if ( $date === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
echo $date;  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a> Exemple  
L’exemple suivant montre comment récupérer la date sous la forme d’un type PHP. `'ReturnDatesAsStrings'=> false` est activé par défaut.  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "SELECT VersionDate FROM AWBuildVersion";  
  
$stmt = sqlsrv_query( $conn, $tsql);  
  
if ( $stmt === false ) {  
   echo "Error in statement preparation/execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_fetch( $stmt );  
  
// retrieve date as string  
$date = sqlsrv_get_field( $stmt, 0 );  
  
if ( $date === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$date_string = date_format( $date, 'jS, F Y' );  
echo "Date = $date_string\n";  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a> Voir aussi  
[Récupération de données](../../connect/php/retrieving-data.md)  
  
