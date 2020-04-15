---
title: SQLConfigDataSource (Chauffeur d’accès) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284049"
---
# <a name="sqlconfigdatasource-access-driver"></a>SQLConfigDataSource (pilote Access)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques à Access Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 La fonction **SQLConfigDataSource** qui est utilisée pour ajouter, modifier ou supprimer une source de données utilise dynamiquement les mots clés suivants.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|La séquence dans laquelle les champs sont triés.<br /><br /> Cela définit la même option que **Collating Sequence** dans la boîte de dialogue de configuration.|  
|COMPACT_DB|Effectue le compactage de données sur un fichier de base de données. A le format suivant: COMPACT_DB<path_name><optionaL_sort_order>> mot-clé ENCRYPT \<en option.<br /><br /> Lors de l’utilisation du mot clé COMPACT_DB dans la même déclaration avec un mot clé DSN, ce pilote ignore le mot clé DSN. Par conséquent, le compactage d’une base de données et la spécifier d’un DSN est un processus en deux étapes.|  
|CREATE_DB|Crée un fichier de base de données. A le format suivant: CREATE_DB<path_name>\<optional_sort><mot clé optional_ENCRYPT>, où le nom du chemin est le chemin complet vers une base de données Microsoft Access. Une erreur sera retournée si le nom du chemin spécifie une base de données existante. L’ordre de tri sera mis en place dans la nouvelle boîte de dialogue database affichée lorsque le bouton Créer est appuyé dans la boîte de dialogue Microsoft Access Setup. Si aucun ordre de tri n’est spécifié, Général est utilisé.<br /><br /> Lors de l’utilisation du mot clé CREATE_DB dans la même déclaration avec un mot clé DSN, ce pilote ignore le mot clé DSN. Par conséquent, la création d’une base de données et la spécit d’un DSN est un processus en deux étapes. Lors de l’utilisation du mot clé CREATE_DB, si le nom de voie de la base de données Microsoft Access à créer contient un ou plusieurs espaces, alors l’ensemble du nom de voie doit être inclus par des marques de double citation, comme indiqué dans les exemples suivants:<br /><br /> "C: 'PROGRAM FILES’COMMON FILES' MyAccess.mdb"<br /><br /> "C:-PROGRAM FILES-Access2.mdb"<br /><br /> CREATE_DB-C : 'TEMP’test.mdb (pas de guillemets nécessaires)|  
|CREATE_SYSDB|Crée un fichier de base de données système. A le format suivant: CREATE_SYSDB\<'nom de voie \<>'option-tri-ordre>, où le nom du chemin est le chemin complet vers une base de données Microsoft Access. Une erreur sera retournée si le nom du chemin spécifie une base de données existante. L’ordre de tri sera mis en place dans la nouvelle boîte de dialogue **database** affichée lorsque le bouton **Créer** est cliqué dans la boîte de dialogue **ODBC Microsoft Access Setup.** Si aucun ordre de tri n’est spécifié, Général est utilisé.|  
|CREATE_V2DB|Crée un fichier de base de données compatible avec Microsoft Access 2.0. A le format suivant:\<CREATE_V2DB -nom de \<chemin>> optionnelle-tri-ordre, où le nom du chemin est le chemin complet vers une base de données Microsoft Access. Une erreur sera retournée si le nom du chemin spécifie une base de données existante. L’ordre de tri sera mis en place dans la nouvelle boîte de dialogue database affichée lorsque le bouton Créer est appuyé dans la boîte de dialogue Microsoft Access Setup. Si aucun ordre de tri n’est spécifié, Général est utilisé.<br /><br /> Lors de l’utilisation du mot clé CREATE_V2DB dans la même déclaration avec un mot clé DSN, ce pilote ignore le mot clé DSN. Par conséquent, la création d’une base de données et la spécit d’un DSN est un processus en deux étapes.<br /><br /> Lors de l’utilisation du mot clé CREATE_V2DB, si le nom de voie de la base de données Microsoft Access à créer contient un ou plusieurs espaces, alors l’ensemble du nom de voie doit être inclus par des marques de double citation, comme indiqué dans les exemples suivants:<br /><br /> "C: 'PROGRAM FILES’COMMON FILES' MyAccess.mdb"<br /><br /> "C:-PROGRAM FILES-Access2.mdb"<br /><br /> CREATE_V2DB-C : 'TEMP’test.mdb (pas de guillemets nécessaires)|  
|DBQ|Le nom du fichier de base de données.<br /><br /> Cela définit la même option que **la base de données** dans la boîte de dialogue de configuration.|  
|DÉFAUTDIR|La spécification de trajectoire au fichier de base de données.|  
|Description|Une description des données dans la source de données.<br /><br /> Cela définit la même option que **description** dans la boîte de dialogue de configuration.|  
|DRIVER|La spécification de chemin au conducteur DLL.|  
|DRIVERID (EN)|Une pièce d’identité pour le conducteur.  25 (Accès Microsoft)|  
|FIL (EN)|Type de fichier MS Access pour Microsoft Access|  
|IMPLICITECOMMITSYNC|Détermine si le pilote Microsoft Access effectuera des commits internes ou implicites asynchrone. Cette valeur est initialement définie à "Oui", ce qui signifie que le pilote Microsoft Access attendra que les commits dans une transaction interne / implicite soient complétés.<br /><br /> La valeur de cette option ne doit pas être modifiée sans un examen attentif des conséquences. Pour plus d’informations sur l’option, consultez le *Guide du programmeur de moteurs microsoft Jet Database Engine*.<br /><br /> Cela définit la même option que **ImplicitCommitSync** dans la boîte de dialogue de configuration.|  
|MAXBUFFERSIZE (EN)|La taille du tampon interne, en kilooctets, qui est utilisé par Microsoft Access pour transférer des données à l’intérieur et à partir du disque. La taille tampon par défaut est 2048 KB (affiché comme 2048). Toute valeur integer divisible par 256 peut être utilisée. Cela définit la même option que **la taille tampon** dans la boîte de dialogue de configuration.|  
|MAXSCANROWS (EN)|Nombre de lignes à numériser lors de la définition du type de données d’une colonne à partir des données existantes.<br /><br /> Un nombre de 1 à 16 peut être entré pour que les lignes puissent être numérisées. La valeur par défaut à 8; s’il est réglé à 0, toutes les lignes sont numérisées. (Un numéro en dehors de la limite retournera une erreur.)<br /><br /> Cela définit la même option que **Rows to Scan** dans la boîte de dialogue de configuration.|  
|PAGETIMEOUT|Spécifie la période de temps, en millisecondes, qu’une page (si elle n’est pas utilisée) reste dans le tampon avant d’être supprimée. La valeur par défaut est de cinq dixièmes de seconde (0,5 seconde). Notez que cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> Cela définit la même option que **Page Timeout** dans la boîte de dialogue de configuration.|  
|PWD|Mot de passe.|  
|READONLY|VRAI pour faire lecture de fichier seulement; FALSE pour faire fichier non lu seulement.<br /><br /> Cela définit la même option que **Lire uniquement** dans la boîte de dialogue de configuration.|  
|REPAIR_DB|Répare une base de données endommagée par une défaillance qui se produit pendant le processus de validation.<br /><br /> Lors de l’utilisation du mot clé REPAIR_DB dans la même déclaration avec un mot clé DSN, ce pilote ignore le mot clé DSN. Par conséquent, la réparation d’une base de données et la spécifier d’un DSN est un processus en deux étapes.|  
|SYSTEMDB (EN)|Pour le pilote Microsoft Access, la spécification de trajectoire vers le fichier de base de données du système.<br /><br /> Cela définit la même option que **la base de données système** dans la boîte de dialogue de configuration.|  
|Fils|Le nombre de fils d’arrière-plan pour le moteur à utiliser. Cette valeur est par défaut à 3, mais peut être modifiée.<br /><br /> Cela définit la même option que **Threads** dans la boîte de dialogue de configuration.|  
|Identificateur d’utilisateur|Pour le pilote Microsoft Access, le nom d’identifiant d’utilisateur utilisé pour la connexion.|  
|USERCOMMITSYNC|Détermine si le pilote Microsoft Access effectuera des transactions définies par l’utilisateur de manière asynchrone. Cette valeur est initialement définie à "Oui", ce qui signifie que le pilote Microsoft Access attendra que les commits dans une transaction définie par l’utilisateur soient complétés.<br /><br /> La valeur de cette option ne doit pas être modifiée sans un examen attentif des conséquences. Pour plus d’informations sur l’option, consultez le *Guide du programmeur de moteurs microsoft Jet Database Engine*.<br /><br /> Cela définit la même option que **UserCommitSync** dans la boîte de dialogue de configuration.|
