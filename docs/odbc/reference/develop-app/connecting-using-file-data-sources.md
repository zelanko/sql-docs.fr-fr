---
title: Connexion à l’aide de sources de données de fichiers (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], file data sources
- SQLDriverConnect function [ODBC], connecting using file data sources
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], file data sources
- file data sources [ODBC]
ms.assetid: 3003f8c2-8be6-41cc-8d9c-612e9bd0f3ae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c752fc3b09c06c68dcc216cacac63744dc3101b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287409"
---
# <a name="connecting-using-file-data-sources"></a>Connexion à l’aide de sources de données de fichier
Les informations de connexion d’une source de données de fichiers sont stockées dans un fichier .dsn. En conséquence, la chaîne de connexion peut être utilisée à plusieurs reprises par un seul utilisateur ou partagée entre plusieurs utilisateurs s’ils ont installé le pilote approprié. Le fichier contient un nom de pilote (ou un autre nom source de données dans le cas d’une source de données de fichier non partageable) et, en option, une chaîne de connexion qui peut être utilisée par **SQLDriverConnect**. Le Gestionnaire de pilote construit la chaîne de connexion pour l’appel à **SQLDriverConnect** à partir des mots clés dans le fichier .dsn.  
  
 Une source de données de fichiers permet à une application de spécifier les options de connexion sans avoir à construire une chaîne de connexion pour une utilisation avec **SQLDriverConnect**. La source de données de fichiers est généralement créée en spécifiant le mot clé **SAVEFILE,** ce qui oblige le gestionnaire de pilote à enregistrer la chaîne de connexion de sortie créée par un appel à **SQLDriverConnect** au fichier .dsn. Cette chaîne de connexion peut être utilisée à plusieurs reprises en appelant **SQLDriverConnect** avec le mot clé **FILEDSN.** Cela simplifie le processus de connexion et fournit une source persistante de la chaîne de connexion.  
  
 Des sources de données de fichiers peuvent également être créées en appelant **SQLCreateDataSource** dans l’installateur DLL. L’information peut être inscrite dans le fichier .dsn en appelant **SQLWriteFileDSN**, et lire à partir du fichier .dsn en appelant **SQLReadFileDSN**; ces deux fonctions sont également dans l’installateur DLL. Pour plus d’informations sur l’installateur DLL, voir [Configuring Data Sources](../../../odbc/reference/install/configuring-data-sources.md).  
  
 Les mots clés utilisés pour les informations de connexion se trouvent dans la section [ODBC] d’un fichier .dsn. Les renseignements minimaux qu’un fichier .dsn partageable aurait dans la section [ODBC] sont le mot clé DRIVER :  
  
```  
DRIVER = SQL Server  
```  
  
 Le fichier shareable .dsn contient habituellement une chaîne de connexion, comme suit :  
  
```  
DRIVER = SQL Server  
UID = Larry  
DATABASE = MyDB  
```  
  
 Lorsque la source de données de fichier est inpartable, le fichier .dsn ne contient qu’un mot clé **DSN.** Lorsque le gestionnaire de conducteur reçoit les informations dans une source de données de fichiers non partageable, il se connecte au besoin à la source de données indiquée par le mot clé **DSN.** Un fichier .dsn inétable contiendrait le mot clé suivant :  
  
```  
DSN = MyDataSource  
```  
  
 La chaîne de connexion utilisée pour une source de données de fichiers est l’union des mots clés spécifiés dans le fichier .dsn et les mots clés spécifiés dans la chaîne de connexion dans l’appel à **SQLDriverConnect**. Si l’un des mots clés du fichier .dsn est en conflit avec les mots clés de la chaîne de connexion, le gestionnaire de pilote décide quelle valeur de mot clé doit être utilisée. Pour plus d’informations, voir [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="see-also"></a>Voir aussi  
 [https://support.microsoft.com/kb/165866](https://support.microsoft.com/kb/165866)
