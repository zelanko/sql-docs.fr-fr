---
title: Obtention de données de type long | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- long data [ODBC]
- fetches [ODBC], long data
- result sets [ODBC], fetching
- SQLGetData function [ODBC], getting long data
- retrieving long data [ODBC]
ms.assetid: 6ccb44bc-8695-4bad-91af-363ef22bdb85
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: da901c22eb26af063397b4af184179ebe5c75924
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298989"
---
# <a name="getting-long-data"></a>Obtention de données de type Long
Les SGBD définissent des *données longues* sous forme de données binaires ou de caractères sur une certaine taille, par exemple 255 caractères. Ces données peuvent être suffisamment petites pour être stockées dans une seule mémoire tampon, telle qu’une description de partie de plusieurs milliers de caractères. Toutefois, il peut être trop long pour être stocké en mémoire, tel que des documents texte longs ou des bitmaps. Comme ces données ne peuvent pas être stockées dans une seule mémoire tampon, elles sont extraites du pilote en parties avec **SQLGetData** après que les autres données de la ligne ont été extraites.  
  
> [!NOTE]  
>  Une application peut en fait récupérer n’importe quel type de données avec **SQLGetData**, pas seulement les données longues, bien que seules les données de caractères et binaires puissent être extraites dans des parties. Toutefois, si les données sont suffisamment petites pour tenir dans une seule mémoire tampon, il n’y a généralement aucune raison d’utiliser **SQLGetData**. Il est beaucoup plus facile de lier une mémoire tampon à la colonne et de laisser le pilote renvoyer les données dans la mémoire tampon.  
  
 Pour extraire des données de type long d’une colonne, une application appelle d’abord **SQLFetchScroll** ou **SQLFetch** pour passer à une ligne et extraire les données pour les colonnes dépendantes. L’application appelle ensuite **SQLGetData**. **SQLGetData** a les mêmes arguments que **SQLBindCol**: un descripteur d’instruction ; Numéro de colonne ; le type de données C, l’adresse et la longueur en octets d’une variable d’application ; et l’adresse d’une mémoire tampon de longueur/d’indicateur. Les deux fonctions ont les mêmes arguments, car elles effectuent essentiellement la même tâche : elles décrivent toutes deux une variable d’application pour le pilote et spécifient que les données d’une colonne particulière doivent être retournées dans cette variable. Les principales différences résident dans le fait que **SQLGetData** est appelé après l’extraction d’une ligne (et parfois appelée *liaison tardive* pour cette raison) et que la liaison spécifiée par **SQLGetData** dure uniquement pour la durée de l’appel.  
  
 En ce qui concerne une seule colonne, **SQLGetData** se comporte comme **SQLFetch**: il récupère les données de la colonne, les convertit en type de la variable d’application et les retourne dans cette variable. Elle retourne également la longueur en octets des données dans la mémoire tampon de longueur/d’indicateur. Pour plus d’informations sur la façon dont **SQLFetch** retourne des données, consultez [extraction d’une ligne de données](../../../odbc/reference/develop-app/fetching-a-row-of-data.md).  
  
 **SQLGetData** diffère de **SQLFetch** dans un respect important. Si elle est appelée plusieurs fois à la suite pour la même colonne, chaque appel retourne une partie successive des données. Chaque appel, à l’exception du dernier appel, retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01004 (String Data, Right TRUNCATE); le dernier appel retourne SQL_SUCCESS. Voici comment **SQLGetData** est utilisé pour extraire des données longues en parties. Lorsqu’il n’y a plus de données à retourner, **SQLGetData** retourne SQL_NO_DATA. L’application est chargée de placer les données longues ensemble, ce qui peut signifier la concaténation des parties des données. Chaque partie se termine par un caractère null ; l’application doit supprimer le caractère de fin null en cas de concaténation des parties. La récupération de données en parties peut être effectuée pour les signets de longueur variable ainsi que pour d’autres données de type long. La valeur retournée dans la mémoire tampon de longueur/d’indicateur diminue dans chaque appel par le nombre d’octets retournés dans l’appel précédent, bien qu’il soit courant que le pilote ne parvient pas à découvrir la quantité de données disponibles et retourne une longueur d’octet de SQL_NO_TOTAL. Par exemple :  
  
```  
// Declare a binary buffer to retrieve 5000 bytes of data at a time.  
SQLCHAR       BinaryPtr[5000];  
SQLUINTEGER   PartID;  
SQLINTEGER    PartIDInd, BinaryLenOrInd, NumBytes;  
SQLRETURN     rc;   
SQLHSTMT      hstmt;  
  
// Create a result set containing the ID and picture of each part.  
SQLExecDirect(hstmt, "SELECT PartID, Picture FROM Pictures", SQL_NTS);  
  
// Bind PartID to the PartID column.  
SQLBindCol(hstmt, 1, SQL_C_ULONG, &PartID, 0, &PartIDInd);  
  
// Retrieve and display each row of data.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   // Display the part ID and initialize the picture.  
   DisplayID(PartID, PartIDInd);  
   InitPicture();  
  
   // Retrieve the picture data in parts. Send each part and the number   
   // of bytes in each part to a function that displays it. The number   
   // of bytes is always 5000 if there were more than 5000 bytes   
   // available to return (cbBinaryBuffer > 5000). Code to check if   
   // rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
   while ((rc = SQLGetData(hstmt, 2, SQL_C_BINARY, BinaryPtr, sizeof(BinaryPtr),  
                           &BinaryLenOrInd)) != SQL_NO_DATA) {  
      NumBytes = (BinaryLenOrInd > 5000) || (BinaryLenOrInd == SQL_NO_TOTAL) ?  
                  5000 : BinaryLenOrInd;  
      DisplayNextPictPart(BinaryPtr, NumBytes);  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```  
  
 Il existe plusieurs restrictions sur l’utilisation de **SQLGetData**. En général, les colonnes accessibles avec **SQLGetData**:  
  
-   Doit être accessible par ordre d’incrémentation du numéro de colonne (en raison de la façon dont les colonnes d’un jeu de résultats sont lues à partir de la source de données). Par exemple, il est erroné d’appeler **SQLGetData** pour la colonne 5, puis de l’appeler pour la colonne 4.  
  
-   Ne peut pas être lié.  
  
-   Le numéro de colonne doit être supérieur à celui de la dernière colonne dépendante. Par exemple, si la dernière colonne dépendante est la colonne 3, c’est une erreur d’appeler **SQLGetData** pour la colonne 2. Pour cette raison, les applications doivent veiller à placer des colonnes de données longues à la fin de la liste de sélection.  
  
-   Ne peut pas être utilisé si **SQLFetch** ou **SQLFetchScroll** a été appelé pour extraire plus d’une ligne. Pour plus d’informations, consultez [utilisation de curseurs de bloc](../../../odbc/reference/develop-app/using-block-cursors.md).  
  
 Certains pilotes n’appliquent pas ces restrictions. Les applications interopérables doivent soit supposer qu’elles existent, soit déterminer les restrictions qui ne sont pas appliquées en appelant **SQLGetInfo** avec l’option SQL_GETDATA_EXTENSIONS.  
  
 Si l’application n’a pas besoin de toutes les données d’une colonne de données binaires ou de caractères, elle peut réduire le trafic réseau dans les pilotes SGBD en définissant l’attribut d’instruction SQL_ATTR_MAX_LENGTH avant d’exécuter l’instruction. Cela limite le nombre d’octets de données qui seront renvoyés pour toute colonne de type caractère ou binaire. Par exemple, supposons qu’une colonne contienne des documents texte longs. Une application qui parcourt la table contenant cette colonne peut être obligée d’afficher uniquement la première page de chaque document. Bien que cet attribut d’instruction puisse être simulé dans le pilote, il n’y a aucune raison de le faire. En particulier, si une application souhaite tronquer des données de type caractère ou binaire, elle doit lier une petite mémoire tampon à la colonne avec **SQLBindCol** et laisser le pilote tronquer les données.
