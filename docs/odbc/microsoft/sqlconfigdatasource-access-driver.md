---
title: SQLConfigDataSource (pilote Access) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLConfigDataSource function [ODBC], Access Driver
- Access driver [ODBC], SQLConfigDataSource
ms.assetid: 1b152fb7-fa12-46b9-b168-006bb1355e77
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 48668525b578845fc330881d7c7de503d69d0928
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81284049"
---
# <a name="sqlconfigdatasource-access-driver"></a>SQLConfigDataSource (pilote Access)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote d’accès. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 La fonction **SQLConfigDataSource** utilisée pour ajouter, modifier ou supprimer une source de données utilise dynamiquement les mots clés suivants.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|Séquence dans laquelle les champs sont triés.<br /><br /> Cela définit la même option que la **séquence de classement** dans la boîte de dialogue de configuration.|  
|COMPACT_DB|Effectue un compactage des données sur un fichier de base de données. A le format suivant : COMPACT_DB =<path_name><optionaL_sort_order>\<> mot clé ENCRYPT facultatif.<br /><br /> Lorsque vous utilisez le mot clé COMPACT_DB dans la même instruction avec un mot clé DSN, ce pilote ignore le mot clé DSN. Par conséquent, le compactage d’une base de données et la spécification d’un DSN sont un processus en deux étapes.|  
|CREATE_DB|Crée un fichier de base de données. A le format suivant : CREATE_DB =<path_name>\<optional_sort-ordre><optional_ENCRYPT mot clé>, où le nom du chemin d’accès est le chemin d’accès complet à une base de données Microsoft Access. Une erreur est retournée si le nom du chemin d’accès spécifie une base de données existante. L’ordre de tri est défini dans la boîte de dialogue nouvelle base de données qui s’affiche lorsque vous appuyez sur le bouton créer dans la boîte de dialogue installation de Microsoft Access. Si aucun ordre de tri n’est spécifié, général est utilisé.<br /><br /> Lorsque vous utilisez le mot clé CREATE_DB dans la même instruction avec un mot clé DSN, ce pilote ignore le mot clé DSN. Par conséquent, la création d’une base de données et la spécification d’un nom de source de données sont un processus en deux étapes. Lorsque vous utilisez le mot clé CREATE_DB, si le nom du chemin d’accès de la base de données Microsoft Access à créer contient un ou plusieurs espaces, alors le chemin d’accès complet doit être placé entre guillemets doubles, comme indiqué dans les exemples suivants :<br /><br /> « C:\PROGRAM FILES\COMMON FILES \ MyAccess. mdb »<br /><br /> « C:\PROGRAM FILES\Access2.mdb »<br /><br /> CREATE_DB = C:\TEMP\test.mdb (sans guillemets)|  
|CREATE_SYSDB|Crée un fichier de base de données système. A le format suivant : CREATE_SYSDB =\<chemin-nom>\<facultatif-ordre de tri>, où le nom du chemin d’accès est le chemin d’accès complet à une base de données Microsoft Access. Une erreur est retournée si le nom du chemin d’accès spécifie une base de données existante. L’ordre de tri est défini dans la boîte **de dialogue nouvelle base de données** qui s’affiche lorsque vous cliquez sur le bouton **créer** dans la boîte de dialogue **installation ODBC pour Microsoft Access** . Si aucun ordre de tri n’est spécifié, général est utilisé.|  
|CREATE_V2DB|Crée un fichier de base de données compatible avec Microsoft Access 2,0. A le format suivant : CREATE_V2DB =\<chemin-nom>\<facultatif-ordre de tri>, où le nom du chemin d’accès est le chemin d’accès complet à une base de données Microsoft Access. Une erreur est retournée si le nom du chemin d’accès spécifie une base de données existante. L’ordre de tri est défini dans la boîte de dialogue nouvelle base de données qui s’affiche lorsque vous appuyez sur le bouton créer dans la boîte de dialogue installation de Microsoft Access. Si aucun ordre de tri n’est spécifié, général est utilisé.<br /><br /> Lorsque vous utilisez le mot clé CREATE_V2DB dans la même instruction avec un mot clé DSN, ce pilote ignore le mot clé DSN. Par conséquent, la création d’une base de données et la spécification d’un nom de source de données sont un processus en deux étapes.<br /><br /> Lorsque vous utilisez le mot clé CREATE_V2DB, si le nom du chemin d’accès de la base de données Microsoft Access à créer contient un ou plusieurs espaces, alors le chemin d’accès complet doit être placé entre guillemets doubles, comme indiqué dans les exemples suivants :<br /><br /> « C:\PROGRAM FILES\COMMON FILES \ MyAccess. mdb »<br /><br /> « C:\PROGRAM FILES\Access2.mdb »<br /><br /> CREATE_V2DB = C:\TEMP\test.mdb (sans guillemets)|  
|DBQ|Nom du fichier de base de données.<br /><br /> Cela définit la même option que **base de données** dans la boîte de dialogue installation.|  
|DEFAULTDIR|Spécification du chemin d’accès au fichier de base de données.|  
|Description|Description des données dans la source de données.<br /><br /> Cela définit la même option que **Description** dans la boîte de dialogue d’installation.|  
|DRIVER|Spécification du chemin d’accès à la DLL du pilote.|  
|DRIVERID|ID d’entier du pilote.  25 (Microsoft Access)|  
|FIL|Type de fichier MS Access pour Microsoft Access|  
|IMPLICITCOMMITSYNC|Détermine si le pilote Microsoft Access effectue des validations internes ou implicites de façon asynchrone. Cette valeur est initialement définie sur « Oui », ce qui signifie que le pilote Microsoft Access attendra que les validations dans une transaction interne/implicite soient terminées.<br /><br /> La valeur de cette option ne doit pas être modifiée sans tenir compte des conséquences. Pour plus d’informations sur cette option, consultez le *Guide du programmeur Microsoft Jet moteur de base de données*.<br /><br /> Cela définit la même option que **ImplicitCommitSync** dans la boîte de dialogue d’installation.|  
|MAXBUFFERSIZE|Taille de la mémoire tampon interne, en kilo-octets, utilisée par Microsoft Access pour transférer des données vers et depuis le disque. La taille de la mémoire tampon par défaut est de 2048 Ko (affichée sous la forme 2048). Toute valeur entière divisible par 256 peut être utilisée. Cela définit la même option que la taille de la **mémoire tampon** dans la boîte de dialogue d’installation.|  
|MAXSCANROWS|Nombre de lignes à analyser lors de la définition du type de données d’une colonne en fonction des données existantes.<br /><br /> Vous pouvez entrer un nombre compris entre 1 et 16 pour les lignes à analyser. La valeur par défaut est 8. Si la valeur est 0, toutes les lignes sont analysées. (Un nombre en dehors de la limite renverra une erreur.)<br /><br /> Cela définit la même option que **lignes à analyser** dans la boîte de dialogue d’installation.|  
|PAGETIMEOUT|Spécifie la durée, en millisecondes, pendant laquelle une page (si elle n’est pas utilisée) reste dans la mémoire tampon avant d’être supprimée. La valeur par défaut est cinq dixièmes de seconde (0,5 secondes). Notez que cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> Cela définit la même option que le **délai d’attente** de la page dans la boîte de dialogue d’installation.|  
|PWD|Mot de passe.|  
|READONLY|TRUE pour rendre le fichier accessible en lecture seule ; FALSe pour que le fichier ne soit pas en lecture seule.<br /><br /> Cela permet de définir la même option en **lecture seule** dans la boîte de dialogue d’installation.|  
|REPAIR_DB|Répare une base de données endommagée par un échec qui se produit pendant le processus de validation.<br /><br /> Lorsque vous utilisez le mot clé REPAIR_DB dans la même instruction avec un mot clé DSN, ce pilote ignore le mot clé DSN. Par conséquent, la réparation d’une base de données et la spécification d’un nom de source de données sont un processus en deux étapes.|  
|SYSTEMDB|Pour le pilote Microsoft Access, la spécification du chemin d’accès au fichier de base de données système.<br /><br /> Cela définit la même option que la **base de données système** dans la boîte de dialogue installation.|  
|THÈMES|Nombre de threads d’arrière-plan à utiliser par le moteur. La valeur par défaut est 3, mais elle peut être modifiée.<br /><br /> Cela définit la même option que les **Threads** dans la boîte de dialogue d’installation.|  
|Identificateur d’utilisateur|Pour le pilote Microsoft Access, nom de l’ID utilisateur utilisé pour la connexion.|  
|USERCOMMITSYNC|Détermine si le pilote Microsoft Access effectue des transactions définies par l’utilisateur de manière asynchrone. Cette valeur est initialement définie sur « Oui », ce qui signifie que le pilote Microsoft Access attendra la fin des validations dans une transaction définie par l’utilisateur.<br /><br /> La valeur de cette option ne doit pas être modifiée sans tenir compte des conséquences. Pour plus d’informations sur cette option, consultez le *Guide du programmeur Microsoft Jet moteur de base de données*.<br /><br /> Cela définit la même option que **UserCommitSync** dans la boîte de dialogue d’installation.|
