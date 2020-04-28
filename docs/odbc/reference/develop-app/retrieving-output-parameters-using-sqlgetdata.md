---
title: Récupération des paramètres de sortie à l’aide de SQLGetData | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], retrieving output parameters
- output parameters [ODBC]
- retrieving output parameters [ODBC]
ms.assetid: 7a8c298a-2160-491d-a300-d36f45568d9c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c96a3f9fc81d081ce16fe8e75746aafe8962fd0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81294589"
---
# <a name="retrieving-output-parameters-using-sqlgetdata"></a>Récupération des paramètres de sortie à l’aide de SQLGetData
Avant ODBC 3,8, une application pouvait uniquement récupérer les paramètres de sortie d’une requête avec une mémoire tampon de sortie liée. Toutefois, il est difficile d’allouer une mémoire tampon très importante lorsque la taille de la valeur de paramètre est très importante (par exemple, une grande image). ODBC 3,8 introduit une nouvelle méthode pour récupérer les paramètres de sortie en plusieurs parties. Une application peut maintenant appeler **SQLGetData** avec une mémoire tampon de petite taille plusieurs fois pour récupérer une valeur de paramètre élevée. Cela est similaire à la récupération de données de grande colonne.  
  
 Pour lier un paramètre de sortie ou un paramètre d’entrée/sortie à récupérer dans des parties, appelez **SQLBindParameter** avec l’argument *InputOutputType* défini sur SQL_PARAM_OUTPUT_STREAM ou SQL_PARAM_INPUT_OUTPUT_STREAM. Avec SQL_PARAM_INPUT_OUTPUT_STREAM, une application peut utiliser **SQLPutData** pour entrer des données dans le paramètre, puis utiliser **SQLGetData** pour récupérer le paramètre de sortie. Les données d’entrée doivent être dans la forme de données en cours d’exécution, à l’aide de **SQLPutData** au lieu de les lier à une mémoire tampon préallouée.  
  
 Cette fonctionnalité peut être utilisée par les applications ODBC 3,8 ou les applications ODBC 3. x et ODBC 2. x recompilées, et ces applications doivent avoir un pilote ODBC 3,8 qui prend en charge la récupération des paramètres de sortie à l’aide de **SQLGetData** et ODBC 3,8 Driver Manager. Pour plus d’informations sur l’activation d’une ancienne application pour utiliser les nouvelles fonctionnalités ODBC, consultez [matrice de compatibilité](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
## <a name="usage-example"></a>Exemple d'utilisation  
 Par exemple, envisagez d’exécuter une procédure stockée, **{CALL sp_f ( ?, ?)}**, où les deux paramètres sont liés en tant que SQL_PARAM_OUTPUT_STREAM, et la procédure stockée ne retourne aucun jeu de résultats (plus loin dans cette rubrique, vous trouverez un scénario plus complexe) :  
  
1.  Pour chaque paramètre, appelez **SQLBindParameter** avec *InputOutputType* défini sur SQL_PARAM_OUTPUT_STREAM et *ParameterValuePtr* défini sur un jeton, tel qu’un numéro de paramètre, un pointeur vers des données ou un pointeur vers une structure utilisée par l’application pour lier les paramètres d’entrée. Cet exemple utilise le numéro de paramètre comme jeton.  
  
2.  Exécutez la requête avec **SQLExecDirect** ou **SQLExecute**. SQL_PARAM_DATA_AVAILABLE est retourné, ce qui indique que des paramètres de sortie diffusés en continu sont disponibles pour la récupération.  
  
3.  Appelez **SQLParamData** pour obtenir le paramètre qui est disponible pour la récupération. **SQLParamData** renverra SQL_PARAM_DATA_AVAILABLE avec le jeton du premier paramètre disponible, qui est défini dans **SQLBindParameter** (étape 1). Le jeton est retourné dans la mémoire tampon vers laquelle pointe le *ValuePtrPtr* .  
  
4.  Appelez **SQLGetData** avec l’argument *col*_OR\_*Param_Num* défini sur le paramètre ordinal pour récupérer les données du premier paramètre disponible. Si **SQLGetData** retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01004 (données tronquées) et que le type est une longueur variable sur le client et le serveur, il y a plus de données à récupérer à partir du premier paramètre disponible. Vous pouvez continuer à appeler **SQLGetData** jusqu’à ce qu’il retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO avec une valeur **SQLSTATE**différente.  
  
5.  Répétez les étapes 3 et 4 pour récupérer le paramètre actuel.  
  
6.  Appelez **SQLParamData** à nouveau. Si elle retourne tout sauf SQL_PARAM_DATA_AVAILABLE, il n’y a plus de données de paramètre diffusées en continu à récupérer et le code de retour est le code de retour de l’instruction suivante qui est exécutée.  
  
7.  Appelez **SQLMoreResults** pour traiter le jeu de paramètres suivant jusqu’à ce qu’il retourne SQL_NO_DATA. **SQLMoreResults** renverra SQL_NO_DATA dans cet exemple si l’attribut d’instruction SQL_ATTR_PARAMSET_SIZE a la valeur 1. Dans le cas contraire, **SQLMoreResults** retourne SQL_PARAM_DATA_AVAILABLE pour indiquer qu’il existe des paramètres de sortie diffusés en continu pour l’ensemble suivant de paramètres à récupérer.  
  
 À l’instar d’un paramètre d’entrée DAE, le jeton utilisé dans l’argument *ParameterValuePtr* dans **SQLBindParameter** (étape 1) peut être un pointeur qui pointe vers une structure de données d’application, qui contient l’ordinal du paramètre et d’autres informations spécifiques à l’application, si nécessaire.  
  
 L’ordre de la sortie diffusée en continu ou des paramètres d’entrée/sortie retournés est spécifique au pilote et peut ne pas toujours être identique à l’ordre spécifié dans la requête.  
  
 Si l’application n’appelle pas **SQLGetData** à l’étape 4, la valeur du paramètre est ignorée. De même, si l’application appelle **SQLParamData** avant qu’une valeur de paramètre ait été lue par **SQLGetData**, le reste de la valeur est ignoré, et l’application peut traiter le paramètre suivant.  
  
 Si l’application appelle **SQLMoreResults** avant le traitement de tous les paramètres de sortie diffusés (**SQLParamData** continue de retourner SQL_PARAM_DATA_AVAILABLE), tous les paramètres restants sont ignorés. De même, si l’application appelle **SQLMoreResults** avant qu’une valeur de paramètre ait été lue par **SQLGetData**, le reste de la valeur et tous les paramètres restants sont ignorés, et l’application peut continuer à traiter le jeu de paramètres suivant.  
  
 Notez qu’une application peut spécifier le type de données C dans **SQLBindParameter** et **SQLGetData**. Le type de données C spécifié avec **SQLGetData** remplace le type de données c spécifié dans **SQLBindParameter**, sauf si le type de données c spécifié dans **SQLGetData** est SQL_APD_TYPE.  
  
 Bien qu’un paramètre de sortie diffusé en continu soit plus utile lorsque le type de données du paramètre de sortie est de type BLOB, cette fonctionnalité peut également être utilisée avec n’importe quel type de données. Les types de données pris en charge par les paramètres de sortie diffusés en continu sont spécifiés dans le pilote.  
  
 S’il y a SQL_PARAM_INPUT_OUTPUT_STREAM paramètres à traiter, **SQLExecute** ou **SQLExecDirect** retourneront SQL_NEED_DATA en premier. Une application peut appeler **SQLParamData** et **SQLPutData** pour envoyer des données de paramètre DAE. Lorsque tous les paramètres d’entrée de DAE sont traités, **SQLParamData** retourne SQL_PARAM_DATA_AVAILABLE pour indiquer que les paramètres de sortie diffusés en continu sont disponibles.  
  
 Lorsqu’il existe des paramètres de sortie diffusés en continu et des paramètres de sortie liés à traiter, le pilote détermine l’ordre de traitement des paramètres de sortie. Ainsi, si un paramètre de sortie est lié à une mémoire tampon (le paramètre **SQLBindParameter** *InputOutputType* a la valeur SQL_PARAM_INPUT_OUTPUT ou SQL_PARAM_OUTPUT), la mémoire tampon ne peut pas être remplie tant que **SQLParamData** ne retourne pas SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO. Une application doit lire une mémoire tampon liée uniquement lorsque **SQLParamData** retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO qui est après le traitement de tous les paramètres de sortie diffusés en continu.  
  
 La source de données peut retourner un avertissement et un jeu de résultats, en plus du paramètre de sortie diffusé en continu. En général, les avertissements et les jeux de résultats sont traités séparément d’un paramètre de sortie transmis en continu en appelant **SQLMoreResults**. Traitez les avertissements et le jeu de résultats avant de traiter le paramètre de sortie diffusé en continu.  
  
 Le tableau suivant décrit les différents scénarios d’une seule commande envoyée au serveur, ainsi que la façon dont l’application doit fonctionner.  
  
|Scénario|Valeur de retour de SQLExecute ou SQLExecDirect|Que faire maintenant ?|  
|--------------|---------------------------------------------------|---------------------|  
|Les données incluent uniquement les paramètres de sortie diffusés en continu|SQL_PARAM_DATA_AVAILABLE|Utilisez **SQLParamData** et **SQLGetData** pour récupérer les paramètres de sortie diffusés en continu.|  
|Les données incluent un jeu de résultats et des paramètres de sortie diffusés en continu|SQL_SUCCESS|Récupérez le jeu de résultats avec **SQLBindCol** et **SQLGetData**.<br /><br /> Appelez **SQLMoreResults** pour commencer à traiter les paramètres de sortie diffusés en continu. Elle doit retourner SQL_PARAM_DATA_AVAILABLE.<br /><br /> Utilisez **SQLParamData** et **SQLGetData** pour récupérer les paramètres de sortie diffusés en continu.|  
|Les données incluent un message d’avertissement et des paramètres de sortie diffusés en continu|SQL_SUCCESS_WITH_INFO|Utilisez **SQLGetDiagRec** et **SQLGetDiagField** pour traiter les messages d’avertissement.<br /><br /> Appelez **SQLMoreResults** pour commencer à traiter les paramètres de sortie diffusés en continu. Elle doit retourner SQL_PARAM_DATA_AVAILABLE.<br /><br /> Utilisez **SQLParamData** et **SQLGetData** pour récupérer les paramètres de sortie diffusés en continu.|  
|Les données incluent un message d’avertissement, un jeu de résultats et des paramètres de sortie diffusés en continu|SQL_SUCCESS_WITH_INFO|Utilisez **SQLGetDiagRec** et **SQLGetDiagField** pour traiter les messages d’avertissement. Appelez ensuite **SQLMoreResults** pour commencer à traiter le jeu de résultats.<br /><br /> Récupérez un jeu de résultats avec **SQLBindCol** et **SQLGetData**.<br /><br /> Appelez **SQLMoreResults** pour commencer à traiter les paramètres de sortie diffusés en continu. **SQLMoreResults** doit retourner SQL_PARAM_DATA_AVAILABLE.<br /><br /> Utilisez **SQLParamData** et **SQLGetData** pour récupérer les paramètres de sortie diffusés en continu.|  
|Interroger avec des paramètres d’entrée de DAE, par exemple, un paramètre d’entrée/sortie (DAE) diffusé|NEED_DATA SQL|Appelez **SQLParamData** et **SQLPutData** pour envoyer les données de paramètre d’entrée du DAE.<br /><br /> Une fois tous les paramètres d’entrée de DAE traités, **SQLParamData** peut retourner tout code de retour que **SQLExecute** et **SQLExecDirect** peuvent retourner. Les cas de cette table peuvent ensuite être appliqués.<br /><br /> Si le code de retour est SQL_PARAM_DATA_AVAILABLE, les paramètres de sortie diffusés en continu sont disponibles. Une application doit rappeler **SQLParamData** pour récupérer le jeton pour le paramètre de sortie diffusé en continu, comme décrit dans la première ligne de ce tableau.<br /><br /> Si le code de retour est SQL_SUCCESS, soit il y a un jeu de résultats à traiter, soit le traitement est terminé.<br /><br /> Si le code de retour est SQL_SUCCESS_WITH_INFO, il y a des messages d’avertissement à traiter.|  
  
 Une fois que **SQLExecute**, **SQLExecDirect**ou **SQLMoreResults** retourne SQL_PARAM_DATA_AVAILABLE, une erreur de séquence de fonction se produit si une application appelle une fonction qui ne figure pas dans la liste suivante :  
  
-   **SQLAllocHandle** / **SQLAllocHandleStd**  
  
-   **SQLDataSources** / **SQLDrivers**  
  
-   **SQLGetInfo** / **SQLGetFunctions** SQLGetInfo  
  
-   **SQLGetConnectAttr** / **SQLGetEnvAttr**SQLGetEnvAttr / **SQLGetDescField**SQLGetDescField / **SQLGetDescRec**  
  
-   **SQLNumParams**  
  
-   **SQLDescribeParam**  
  
-   **SQLNativeSql**  
  
-   **SQLParamData**  
  
-   **SQLMoreResults**  
  
-   **SQLGetDiagField** / **SQLGetDiagRec**  
  
-   **SQLCancel**  
  
-   **SQLCancelHandle** (avec descripteur d’instruction)  
  
-   **SQLFreeStmt** (avec l’Option = SQL_CLOSE, SQL_DROP ou SQL_UNBIND)  
  
-   **SQLCloseCursor**  
  
-   **SQLDisconnect**  
  
-   **SQLFreeHandle** (avec comme handletype = SQL_HANDLE_STMT)  
  
-   **SQLGetStmtAttr**  
  
 Les applications peuvent toujours utiliser **SQLSetDescField** ou **SQLSetDescRec** pour définir les informations de liaison. Le mappage de champs ne sera pas modifié. Toutefois, les champs à l’intérieur du descripteur peuvent retourner de nouvelles valeurs. Par exemple, SQL_DESC_PARAMETER_TYPE peut retourner SQL_PARAM_INPUT_OUTPUT_STREAM ou SQL_PARAM_OUTPUT_STREAM.  
  
## <a name="usage-scenario-retrieve-an-image-in-parts-from-a-result-set"></a>Scénario d’utilisation : récupérer une image en plusieurs parties à partir d’un jeu de résultats  
 **SQLGetData** peut être utilisé pour obtenir des données dans des parties lorsqu’une procédure stockée retourne un jeu de résultats qui contient une ligne de métadonnées sur une image et que l’image est retournée dans un paramètre de sortie volumineux.  
  
```  
// CREATE PROCEDURE SP_TestOutputPara  
//      @ID_of_picture   as int,  
//      @Picture         as varbinary(max) out  
// AS  
//     output the image data through streamed output parameter  
// GO  
BOOL displayPicture(SQLUINTEGER idOfPicture, SQLHSTMT hstmt) {  
   SQLLEN      lengthOfPicture;    // The actual length of the picture.  
   BYTE        smallBuffer[100];   // A very small buffer.  
   SQLRETURN   retcode, retcode2;  
  
   // Bind the first parameter (input parameter)  
   SQLBindParameter(  
         hstmt,  
         1,                         // The first parameter.   
         SQL_PARAM_INPUT,           // Input parameter: The ID_of_picture.  
         SQL_C_ULONG,               // The C Data Type.  
         SQL_INTEGER,               // The SQL Data Type.  
         0,                         // ColumnSize is ignored for integer.  
         0,                         // DecimalDigits is ignored for integer.  
         &idOfPicture,              // The Address of the buffer for the input parameter.  
         0,                         // BufferLength is ignored for integer.  
         NULL);                     // This is ignored for integer.  
  
   // Bind the streamed output parameter.  
   SQLBindParameter(  
         hstmt,   
         2,                         // The second parameter.  
         SQL_PARAM_OUTPUT_STREAM,   // A streamed output parameter.   
         SQL_C_BINARY,              // The C Data Type.    
         SQL_VARBINARY,             // The SQL Data Type.  
         0,                         // ColumnSize: The maximum size of varbinary(max).  
         0,                         // DecimalDigits is ignored for binary type.  
         (SQLPOINTER)2,             // ParameterValuePtr: An application-defined  
                                    // token (this will be returned from SQLParamData).  
                                    // In this example, we used the ordinal   
                                    // of the parameter.  
         0,                         // BufferLength is ignored for streamed output parameters.  
         &lengthOfPicture);         // StrLen_or_IndPtr: The status variable returned.   
  
   retcode = SQLPrepare(hstmt, L"{call SP_TestOutputPara(?, ?)}", SQL_NTS);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   retcode = SQLExecute(hstmt);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   // Assume that the retrieved picture exists.  Use SQLBindCol or SQLGetData to retrieve the result-set.  
  
   // Process the result set and move to the streamed output parameters.  
   retcode = SQLMoreResults( hstmt );  
  
   // SQLGetData retrieves and displays the picture in parts.  
   // The streamed output parameter is available.  
   while (retcode == SQL_PARAM_DATA_AVAILABLE) {  
      SQLPOINTER token;   // Output by SQLParamData.  
      SQLLEN cbLeft;      // #bytes remained  
      retcode = SQLParamData(hstmt, &token);   // returned token is 2 (according to the binding)  
      if ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
         // A do-while loop retrieves the picture in parts.  
         do {  
            retcode2 = SQLGetData(   
               hstmt,   
               (UWORD) token,          // the value of the token is the ordinal.   
               SQL_C_BINARY,           // The C-type.  
               smallBuffer,            // A small buffer.   
               sizeof(smallBuffer),    // The size of the buffer.  
               &cbLeft);               // How much data we can get.  
         }  
         while ( retcode2 == SQL_SUCCESS_WITH_INFO );  
      }  
   }  
  
   return TRUE;  
}  
```  
  
## <a name="usage-scenario-send-and-receive-a-large-object-as-a-streamed-inputoutput-parameter"></a>Scénario d’utilisation : envoyer et recevoir un Large Object en tant que paramètre d’entrée/sortie transmis en continu  
 **SQLGetData** peut être utilisé pour obtenir et envoyer des données dans des parties lorsqu’une procédure stockée passe un objet volumineux en tant que paramètre d’entrée/sortie, en diffusant en continu la valeur vers et depuis la base de données. Vous n’avez pas besoin de stocker toutes les données en mémoire.  
  
```  
// CREATE PROCEDURE SP_TestInOut  
//       @picture as varbinary(max) out  
// AS  
//    output the image data through output parameter   
// go  
  
BOOL displaySimilarPicture(BYTE* image, ULONG lengthOfImage, SQLHSTMT hstmt) {  
   BYTE smallBuffer[100];   // A very small buffer.  
   SQLRETURN retcode, retcode2;  
   SQLLEN statusOfPicture;  
  
   // First bind the parameters, before preparing the statement that binds the output streamed parameter.  
   SQLBindParameter(  
      hstmt,   
      1,                                 // The first parameter.  
      SQL_PARAM_INPUT_OUTPUT_STREAM,     // I/O-streamed parameter: The Picture.  
      SQL_C_BINARY,                      // The C Data Type.  
      SQL_VARBINARY,                     // The SQL Data Type.  
      0,                                 // ColumnSize: The maximum size of varbinary(max).  
      0,                                 // DecimalDigits is ignored.   
      (SQLPOINTER)1,                     // An application defined token.   
      0,                                 // BufferLength is ignored for streamed I/O parameters.  
      &statusOfPicture);                 // The status variable.  
  
   statusOfPicture = SQL_DATA_AT_EXEC;   // Input data in parts (DAE parameter at input).  
  
   retcode = SQLPrepare(hstmt, L"{call SP_TestInOut(?) }", SQL_NTS);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   // Execute the statement.  
   retcode = SQLExecute(hstmt);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   if ( retcode == SQL_NEED_DATA ) {  
      // Use SQLParamData to loop through DAE input parameters.  For  
      // each, use SQLPutData to send the data to database in parts.  
  
      // This example uses an I/O parameter with streamed output.  
      // Therefore, the last call to SQLParamData should return  
      // SQL_PARAM_DATA_AVAILABLE to indicate the end of the input phrase   
      // and report that a streamed output parameter is available.  
  
      // Assume retcode is set to the return value of the last call to  
      // SQLParamData, which is equal to SQL_PARAM_DATA_AVAILABLE.  
   }  
  
   // Start processing the streamed output parameters.  
   while ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
      SQLPOINTER token;   // Output by SQLParamData.  
      SQLLEN cbLeft;     // #bytes remained  
      retcode = SQLParamData(hstmt, &token);  
      if ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
         do {  
            retcode2 = SQLGetData(   
               hstmt,   
               (UWORD) token,          // the value of the token is the ordinal.   
               SQL_C_BINARY,           // The C-type.  
               smallBuffer,            // A small buffer.   
               sizeof(smallBuffer),    // The size of the buffer.  
               &cbLeft);               // How much data we can get.  
         }  
         while ( retcode2 == SQL_SUCCESS_WITH_INFO );  
      }  
   }   
  
   return TRUE;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres des instructions](../../../odbc/reference/develop-app/statement-parameters.md)
