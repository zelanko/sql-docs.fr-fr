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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: eeb8fae9c563e675499dec47839acdd0a003765a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020511"
---
# <a name="retrieving-output-parameters-using-sqlgetdata"></a>Récupération des paramètres de sortie à l’aide de SQLGetData
Avant d’ODBC 3.8, une application peut récupérer uniquement les paramètres de sortie d’une requête avec une mémoire tampon de sortie lié. Toutefois, il est difficile à allouer un tampon de très grand lorsque la taille de la valeur du paramètre est très important (par exemple, il s’agit d’une grande image). ODBC 3.8 introduit une nouvelle façon de récupérer les paramètres de sortie dans les parties. Une application peut désormais appeler **SQLGetData** avec une petite mémoire tampon plusieurs fois afin de récupérer une valeur de paramètre élevée. Cela est similaire à la récupération des données de la colonne de grande taille.  
  
 Pour lier un paramètre de sortie ou d’un paramètre d’entrée/sortie doivent être extraites par les parties, appelez **SQLBindParameter** avec la *InputOutputType* argument défini à SQL_PARAM_OUTPUT_STREAM ou SQL_PARAM_INPUT_OUTPUT _STREAM. SQL_PARAM_INPUT_OUTPUT_STREAM, une application peut utiliser **SQLPutData** pour entrer des données dans le paramètre, puis utilisez **SQLGetData** pour récupérer le paramètre de sortie. Les données d’entrée doivent être dans le data-at-execution (DAE) former, à l’aide de **SQLPutData** au lieu de lier à une mémoire tampon préallouée.  
  
 Cette fonctionnalité peut être utilisée par les applications ODBC 3.8 ou recompilée ODBC 3.x et les applications ODBC 2.x et ces applications doivent avoir un pilote ODBC 3.8 qui prend en charge la récupération des paramètres de sortie à l’aide de **SQLGetData** et ODBC 3.8 pilote Gestionnaire. Pour plus d’informations sur l’activation d’une application plus ancienne à utiliser les nouvelles fonctionnalités d’ODBC, consultez [matrice de compatibilité](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
## <a name="usage-example"></a>Exemple d'utilisation  
 Par exemple, envisagez d’exécuter une procédure stockée, **{appel sp_f(?,?)}** , où les deux paramètres sont liées en tant que SQL_PARAM_OUTPUT_STREAM, et la procédure stockée ne retourne aucun jeu de résultats (plus loin dans cette rubrique vous trouverez un scénario plus complexe) :  
  
1.  Pour chaque paramètre, appelez **SQLBindParameter** avec *InputOutputType* défini sur SQL_PARAM_OUTPUT_STREAM et *ParameterValuePtr* définie sur un jeton, telle qu’un numéro de paramètre , un pointeur vers les données, ou un pointeur vers une structure de l’application utilise pour lier les paramètres d’entrée. Cet exemple utilisera la position ordinale du paramètre en tant que le jeton.  
  
2.  Exécutez la requête avec **SQLExecDirect** ou **SQLExecute**. SQL_PARAM_DATA_AVAILABLE s’affichera, en indiquant que les paramètres de sortie diffusées en continu sont disponibles pour la récupération.  
  
3.  Appelez **SQLParamData** pour obtenir le paramètre est disponible pour la récupération. **SQLParamData** retournera SQL_PARAM_DATA_AVAILABLE avec le jeton du premier paramètre disponible qui est défini dans **SQLBindParameter** (étape 1). Le jeton est retourné dans la mémoire tampon qui le *ValuePtrPtr* pointe vers.  
  
4.  Appelez **SQLGetData** avec l’argument *Col*_or\_*Param_Num* la valeur du paramètre ordinale pour récupérer les données du premier paramètre disponible. Si **SQLGetData** retourne SQL_SUCCESS_WITH_INFO et SQLState 01004 (données tronquées) et le type est de longueur variable sur le client et le serveur, il n’existe plus de données à récupérer à partir du premier paramètre disponible. Vous pouvez continuer à appeler **SQLGetData** jusqu'à ce qu’il retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO avec une autre **SQLState**.  
  
5.  Répétez les étapes 3 et 4 pour récupérer le paramètre actuel.  
  
6.  Appelez **SQLParamData** à nouveau. S’il retourne rien sauf SQL_PARAM_DATA_AVAILABLE, il est transmis en continu n’y a plus de données de paramètre à récupérer, et le code de retour sera le code de retour de l’instruction suivante est exécutée.  
  
7.  Appelez **SQLMoreResults** pour traiter l’ensemble de paramètres suivant jusqu'à ce qu’il retourne SQL_NO_DATA. **SQLMoreResults** retourne SQL_NO_DATA dans cet exemple si l’attribut d’instruction SQL_ATTR_PARAMSET_SIZE a été défini sur 1. Sinon, **SQLMoreResults** retournera SQL_PARAM_DATA_AVAILABLE pour indiquer que les paramètres de sortie diffusées en continu sont disponibles pour l’ensemble suivant de paramètres à récupérer.  
  
 Similaire à un paramètre d’entrée DAE, le jeton utilisé dans l’argument *ParameterValuePtr* dans **SQLBindParameter** (étape 1) peut être un pointeur qui pointe vers une structure de données d’application, qui contient le ordinal du paramètre et plus d’informations spécifiques à l’application, si nécessaire.  
  
 L’ordre des paramètres d’entrée/sortie retourné de sortie diffusées en continu est spécifiques aux pilotes et peut être pas toujours le même que l’ordre spécifié dans la requête.  
  
 Si l’application n’appelle pas **SQLGetData** à l’étape 4, la valeur du paramètre est ignorée. De même, si l’application appelle **SQLParamData** avant que la totalité d’un paramètre de valeur a été lue par **SQLGetData**, le reste de la valeur est ignoré et l’application peut traiter la prochaine paramètre.  
  
 Si l’application appelle **SQLMoreResults** avant la sortie diffusées en continu tous les paramètres sont traités (**SQLParamData** retourne toujours SQL_PARAM_DATA_AVAILABLE), tous les paramètres restants sont ignorés. De même, si l’application appelle **SQLMoreResults** avant que la totalité d’un paramètre de valeur a été lue par **SQLGetData**, le reste de la valeur et tous les paramètres restants est ignoré et le application peut continuer à traiter le jeu de paramètres suivant.  
  
 Notez qu’une application peut spécifier le type de données C dans les deux **SQLBindParameter** et **SQLGetData**. Le type de données C spécifié avec **SQLGetData** remplace le type de données C spécifié dans **SQLBindParameter**, sauf si le type de données C spécifié dans **SQLGetData** est SQL_APD_TYPE.  
  
 Bien qu’un paramètre de sortie diffusées en continu est plus utile lorsque le type de données du paramètre de sortie est de type BLOB, cette fonctionnalité peut également servir avec n’importe quel type de données. Les types de données pris en charge par les paramètres de sortie diffusées en continu sont spécifiés dans le pilote.  
  
 S’il existe des paramètres SQL_PARAM_INPUT_OUTPUT_STREAM à traiter, **SQLExecute** ou **SQLExecDirect** retourne SQL_NEED_DATA tout d’abord. Une application peut appeler **SQLParamData** et **SQLPutData** pour envoyer des données de paramètre DAE. Lorsque tous les paramètres d’entrée DAE sont traitées, **SQLParamData** retourne SQL_PARAM_DATA_AVAILABLE pour indiquer les paramètres de sortie diffusées en continu sont disponibles.  
  
 Lorsqu’il sont diffusés en continu les paramètres de sortie et les paramètres de sortie lié à traiter, le pilote détermine l’ordre de traitement des paramètres de sortie. Par conséquent, si un paramètre de sortie est lié à une mémoire tampon (la **SQLBindParameter** paramètre *InputOutputType* est définie sur SQL_PARAM_INPUT_OUTPUT ou SQL_PARAM_OUTPUT), la mémoire tampon ne peut pas être remplie jusqu'à  **SQLParamData** retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO. Une application doit lire une limite de mémoire tampon qu’après **SQLParamData** retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO est diffusée après tous les paramètres de sortie sont traités.  
  
 La source de données peut renvoyer qu'un avertissement et le résultat définies, en plus du paramètre de sortie diffusées en continu. En règle générale, les jeux de résultats et les avertissements sont traités séparément à partir d’un paramètre de sortie diffusées en continu en appelant **SQLMoreResults**. Avertissements de processus et le jeu de résultats avant traitement du paramètre de sortie diffusées en continu.  
  
 Le tableau suivant décrit les différents scénarios d’une seule commande envoyée au serveur et le fonctionne de l’application.  
  
|Scénario|Valeur de retour SQLExecute ou SQLExecDirect|Que faire ensuite|  
|--------------|---------------------------------------------------|---------------------|  
|Données comprennent uniquement des paramètres de sortie diffusées en continu|SQL_PARAM_DATA_AVAILABLE|Utilisez **SQLParamData** et **SQLGetData** pour récupérer les paramètres de sortie diffusées en continu.|  
|Données inclut un jeu de résultats et transmis en continu de paramètres de sortie|SQL_SUCCESS|Récupérer le jeu de résultats avec **SQLBindCol** et **SQLGetData**.<br /><br /> Appelez **SQLMoreResults** pour démarrer le traitement des paramètres de sortie diffusées en continu. Elle doit retourner SQL_PARAM_DATA_AVAILABLE.<br /><br /> Utilisez **SQLParamData** et **SQLGetData** pour récupérer les paramètres de sortie diffusées en continu.|  
|Données inclut un message d’avertissement et transmis en continu de paramètres de sortie|SQL_SUCCESS_WITH_INFO|Utilisez **SQLGetDiagRec** et **SQLGetDiagField** pour traiter les messages avertissement.<br /><br /> Appelez **SQLMoreResults** pour démarrer le traitement des paramètres de sortie diffusées en continu. Elle doit retourner SQL_PARAM_DATA_AVAILABLE.<br /><br /> Utilisez **SQLParamData** et **SQLGetData** pour récupérer les paramètres de sortie diffusées en continu.|  
|Les données incluent un message d’avertissement, le jeu de résultats et diffusé en continu des paramètres de sortie|SQL_SUCCESS_WITH_INFO|Utilisez **SQLGetDiagRec** et **SQLGetDiagField** pour traiter les messages avertissement. Appelez ensuite **SQLMoreResults** doit commencer à traiter le résultat de jeu.<br /><br /> Récupérer un jeu de résultats avec **SQLBindCol** et **SQLGetData**.<br /><br /> Appelez **SQLMoreResults** pour démarrer le traitement des paramètres de sortie diffusées en continu. **SQLMoreResults** doit retourner SQL_PARAM_DATA_AVAILABLE.<br /><br /> Utilisez **SQLParamData** et **SQLGetData** pour récupérer les paramètres de sortie diffusées en continu.|  
|Paramètre de requête avec des paramètres d’entrée DAE, par exemple, un en flux continu d’entrée/sortie (DAE)|SQL NEED_DATA|Appelez **SQLParamData** et **SQLPutData** pour envoyer DAE d’entrée de données de paramètre.<br /><br /> Une fois que tous les paramètres d’entrée DAE sont traités, **SQLParamData** peut retourner un code de retour qui **SQLExecute** et **SQLExecDirect** peut retourner. Les cas dans cette table peuvent ensuite être appliqués.<br /><br /> Si le code de retour est SQL_PARAM_DATA_AVAILABLE, les paramètres de sortie diffusées en continu sont disponibles. Une application doit appeler **SQLParamData** à nouveau pour récupérer le jeton pour le paramètre de sortie diffusées en continu, comme décrit dans la première ligne de cette table.<br /><br /> Si le code de retour est SQL_SUCCESS, il existe un jeu de résultats à traiter ou le traitement est terminé.<br /><br /> Si le code de retour est SQL_SUCCESS_WITH_INFO, il existe des messages d’avertissement à traiter.|  
  
 Après avoir **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** retourne SQL_PARAM_DATA_AVAILABLE, une erreur de séquence de fonction se produira si une application appelle un fonction qui n’est pas dans la liste suivante :  
  
-   **SQLAllocHandle** / **SQLAllocHandleStd**  
  
-   **SQLDataSources** / **SQLDrivers**  
  
-   **SQLGetInfo** / **SQLGetFunctions**  
  
-   **SQLGetConnectAttr** / **SQLGetEnvAttr** / **SQLGetDescField** / **SQLGetDescRec**  
  
-   **SQLNumParams**  
  
-   **SQLDescribeParam**  
  
-   **SQLNativeSql**  
  
-   **SQLParamData**  
  
-   **SQLMoreResults**  
  
-   **SQLGetDiagField** / **SQLGetDiagRec**  
  
-   **SQLCancel**  
  
-   **SQLCancelHandle** (avec le descripteur d’instruction)  
  
-   **SQLFreeStmt** (avec l’Option = SQL_CLOSE, SQL_DROP ou SQL_UNBIND)  
  
-   **SQLCloseCursor**  
  
-   **SQLDisconnect**  
  
-   **SQLFreeHandle** (avec HandleType = SQL_HANDLE_STMT)  
  
-   **SQLGetStmtAttr**  
  
 Les applications peuvent toujours utiliser **SQLSetDescField** ou **SQLSetDescRec** pour définir les informations de liaison. Mappage de champ ne sera pas modifié. Toutefois, les champs à l’intérieur du descripteur peuvent retourner des nouvelles valeurs. Par exemple, SQL_DESC_PARAMETER_TYPE peut retourner SQL_PARAM_INPUT_OUTPUT_STREAM ou SQL_PARAM_OUTPUT_STREAM.  
  
## <a name="usage-scenario-retrieve-an-image-in-parts-from-a-result-set"></a>Scénario d’utilisation : Récupérer une Image dans les parties à partir d’un jeu de résultats  
 **SQLGetData** peut être utilisé pour obtenir des données en parties lorsqu’une procédure stockée retourne un jeu de résultats qui contient une ligne de métadonnées sur une image et l’image est retourné dans un paramètre de sortie volumineux.  
  
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
  
## <a name="usage-scenario-send-and-receive-a-large-object-as-a-streamed-inputoutput-parameter"></a>Scénario d’utilisation : Envoyer et recevoir un objet volumineux comme paramètre d’entrée/sortie en continu  
 **SQLGetData** peut être utilisé pour recevoir et envoyer des données en parties lorsqu’une procédure stockée passe un objet volumineux comme paramètre d’entrée/sortie, la valeur vers et à partir de la base de données de diffusion en continu. Il est inutile de stocker toutes les données en mémoire.  
  
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
