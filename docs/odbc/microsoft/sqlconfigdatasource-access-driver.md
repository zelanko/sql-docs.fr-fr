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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 85b515ed4c30d68e62a49e1044c4ddf6f5cc5ab1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67985236"
---
# <a name="sqlconfigdatasource-access-driver"></a>SQLConfigDataSource (pilote Access)
> [!NOTE]  
>  Cette rubrique fournit des informations d’accès spécifiques au pilote. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le **SQLConfigDataSource** fonction qui est utilisée pour ajouter, modifier ou supprimer une source de données utilise dynamiquement les mots clés suivants.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|La séquence dans laquelle les champs sont triés.<br /><br /> La même option est définie en tant que **séquence de classement** dans la boîte de dialogue d’installation.|  
|COMPACT_DB|Effectue une compression de données sur un fichier de base de données. A le format suivant : COMPACT_DB = < nom_chemin >< optionaL_sort_order >\<mot clé de chiffrement facultatif >.<br /><br /> Lorsque vous utilisez le mot clé COMPACT_DB dans la même instruction avec un mot clé DSN, ce pilote ignore le mot clé DSN. Par conséquent, le compactage d’une base de données et en spécifiant un DSN sont un processus en deux étapes.|  
|CREATE_DB|Crée un fichier de base de données. A le format suivant : CREATE_DB = < nom_chemin >\<optional_sort-ordre >< optional_ENCRYPT mot clé >, où le nom de chemin d’accès est le chemin d’accès complet à une base de données Microsoft Access. Une erreur est renvoyée si le nom de chemin d’accès spécifie une base de données existante. L’ordre de tri sera à tel que défini dans la boîte de dialogue Nouvelle base de données affichée lorsque le bouton Créer est enfoncé dans la boîte de dialogue d’installation de Microsoft Access. Si aucun ordre de tri n’est spécifié, le général est utilisé.<br /><br /> Lorsque vous utilisez le mot clé CREATE_DB dans la même instruction avec un mot clé DSN, ce pilote ignore le mot clé DSN. Par conséquent, la création d’une base de données et en spécifiant un DSN sont un processus en deux étapes. Lorsque vous utilisez le mot clé CREATE_DB, si le chemin d’accès de la base de données Microsoft Access doit être créé contient un ou plusieurs espaces, puis le nom de chemin complet doit être placé entre guillemets doubles, comme indiqué dans les exemples suivants :<br /><br /> « C:\PROGRAM FILES\COMMON Files\Microsoft MyAccess.mdb »<br /><br /> « C:\PROGRAM FILES\Access2.mdb »<br /><br /> CREATE_DB=C:\TEMP\test.mdb (sans guillemets nécessités)|  
|CREATE_SYSDB|Crée un fichier de base de données système. A le format suivant : CREATE_SYSDB =\<nom de chemin d’accès >\<ordre de tri facultatif >, où le nom de chemin d’accès est le chemin d’accès complet à une base de données Microsoft Access. Une erreur est renvoyée si le nom de chemin d’accès spécifie une base de données existante. L’ordre de tri sera en tant que jeu de configuration dans le **nouvelle base de données** boîte de dialogue affichée lorsque la **créer** clic est effectué dans le **ODBC Microsoft Access Setup** boîte de dialogue. Si aucun ordre de tri n’est spécifié, le général est utilisé.|  
|CREATE_V2DB|Crée un fichier de base de données qui est compatible avec Microsoft Access 2.0. A le format suivant : CREATE_V2DB =\<nom de chemin d’accès >\<ordre de tri facultatif >, où le nom de chemin d’accès est le chemin d’accès complet à une base de données Microsoft Access. Une erreur est renvoyée si le nom de chemin d’accès spécifie une base de données existante. L’ordre de tri sera à tel que défini dans la boîte de dialogue Nouvelle base de données affichée lorsque le bouton Créer est enfoncé dans la boîte de dialogue d’installation de Microsoft Access. Si aucun ordre de tri n’est spécifié, le général est utilisé.<br /><br /> Lorsque vous utilisez le mot clé CREATE_V2DB dans la même instruction avec un mot clé DSN, ce pilote ignore le mot clé DSN. Par conséquent, la création d’une base de données et en spécifiant un DSN sont un processus en deux étapes.<br /><br /> Lorsque vous utilisez le mot clé CREATE_V2DB, si le chemin d’accès de la base de données Microsoft Access doit être créé contient un ou plusieurs espaces, puis le nom de chemin complet doit être placé entre guillemets doubles, comme indiqué dans les exemples suivants :<br /><br /> « C:\PROGRAM FILES\COMMON Files\Microsoft MyAccess.mdb »<br /><br /> « C:\PROGRAM FILES\Access2.mdb »<br /><br /> CREATE_V2DB=C:\TEMP\test.mdb (sans guillemets nécessités)|  
|DBQ|Le nom du fichier de base de données.<br /><br /> La même option est définie en tant que **base de données** dans la boîte de dialogue d’installation.|  
|DEFAULTDIR|La spécification de chemin d’accès au fichier de base de données.|  
|Description|Une description des données dans la source de données.<br /><br /> La même option est définie en tant que **Description** dans la boîte de dialogue d’installation.|  
|DRIVER|La spécification de chemin d’accès à la DLL du pilote.|  
|DRIVERID|Un ID d’entier pour le pilote.  25 (Microsoft Access)|  
|FIL|Fichier de type MS Access pour Microsoft Access|  
|IMPLICITCOMMITSYNC|Détermine si le pilote Microsoft Access va effectuer validations internes ou implicites de façon asynchrone. Cette valeur est initialement définie sur « Oui », ce qui signifie que le pilote Microsoft Access attendra les validations dans une transaction interne/implicite pour être terminés.<br /><br /> La valeur de cette option ne doit pas être modifiée sans une attention particulière des conséquences. Pour plus d’informations sur l’option, consultez la *-Guide du programmeur moteur Microsoft Jet de base de données*.<br /><br /> La même option est définie en tant que **ImplicitCommitSync** dans la boîte de dialogue d’installation.|  
|MAXBUFFERSIZE|La taille de la mémoire tampon interne, en kilo-octets, qui est utilisé par Microsoft Access pour transférer des données vers et depuis le disque. La taille de mémoire tampon par défaut est de 2 048 Ko (affiché en tant que 2048). Toute valeur entière divisible par 256 peut être utilisé. La même option est définie en tant que **taille de mémoire tampon** dans la boîte de dialogue d’installation.|  
|MAXSCANROWS|Le nombre de lignes à analyser lors de la définition de type de données d’une colonne en fonction des données existantes.<br /><br /> Nombre compris entre 1 et 16 pouvant être entré pour les lignes à balayer. La valeur par défaut est 8 ; Si elle est définie sur 0, toutes les lignes sont analysées. (Un nombre en dehors de la limite retournera une erreur).<br /><br /> La même option est définie en tant que **lignes à balayer** dans la boîte de dialogue d’installation.|  
|PAGETIMEOUT|Spécifie la période de temps, en millisecondes, d’une page (si non utilisé) reste dans la mémoire tampon avant d’être supprimés. La valeur par défaut est cinq dixièmes de seconde (0,5 seconde). Notez que cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> La même option est définie en tant que **Page Timeout** dans la boîte de dialogue d’installation.|  
|PWD|Mot de passe.|  
|READONLY|TRUE pour rendre le fichier en lecture seule ; FALSE pour rendre le fichier pas en lecture seule.<br /><br /> La même option est définie en tant que **en lecture seule** dans la boîte de dialogue d’installation.|  
|REPAIR_DB|Répare une base de données endommagée par une défaillance se produit pendant le processus de validation.<br /><br /> Lorsque vous utilisez le mot clé REPAIR_DB dans la même instruction avec un mot clé DSN, ce pilote ignore le mot clé DSN. Par conséquent, la réparation d’une base de données et en spécifiant un DSN sont un processus en deux étapes.|  
|SYSTEMDB|Pour le pilote Microsoft Access, la spécification de chemin d’accès au fichier de base de données système.<br /><br /> La même option est définie en tant que **base de données système** dans la boîte de dialogue d’installation.|  
|THREADS|Le nombre de threads d’arrière-plan pour le moteur à utiliser. Cette valeur par défaut est 3, mais peut être modifiée.<br /><br /> La même option est définie en tant que **Threads** dans la boîte de dialogue d’installation.|  
|UID|Pour le pilote Microsoft Access, le nom d’ID utilisateur utilisé pour la connexion.|  
|USERCOMMITSYNC|Détermine si le pilote Microsoft Access va effectuer les transactions définies par l’utilisateur de façon asynchrone. Cette valeur est initialement définie sur « Oui », ce qui signifie que le pilote Microsoft Access attendra les validations dans une transaction définie par l’utilisateur à effectuer.<br /><br /> La valeur de cette option ne doit pas être modifiée sans une attention particulière des conséquences. Pour plus d’informations sur l’option, consultez la *-Guide du programmeur moteur Microsoft Jet de base de données*.<br /><br /> La même option est définie en tant que **UserCommitSync** dans la boîte de dialogue d’installation.|
