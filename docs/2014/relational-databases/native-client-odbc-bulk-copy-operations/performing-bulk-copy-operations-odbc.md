---
title: Exécution d’opérations de copie en bloc (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC]
- ODBC, bulk copy operations
- minimally logged operations [SQL Server Native Client]
- bulk copy [ODBC], about bulk copy
ms.assetid: 5c793405-487c-4f52-88b8-0091d529afb3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 25144e13b4e129209356d0e4e4ebe37f9a3c5d1c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63200813"
---
# <a name="performing-bulk-copy-operations-odbc"></a>Exécution d'opérations de copie en bloc (ODBC)
  Par défaut, ODBC ne prend pas directement en charge les opérations de copie en bloc [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. En cas de connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 ou ultérieure, le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge les fonctions de la bibliothèque de bases de données qui effectuent les opérations de copie en bloc [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette extension spécifique au pilote fournit un chemin d'accès de mise à niveau simple pour les applications de bibliothèque de bases de données existantes qui utilisent les fonctions de copie en bloc. La copie en bloc spécialisée est prise en charge dans les fichiers suivants :  
  
-   sqlncli.h  
  
     Inclut les prototypes de fonction et les définitions de constante pour les fonctions de copie en bloc. sqlncli.h doit être inclus dans l'application ODBC exécutant les opérations de copie en bloc et se trouver dans le chemin d'accès Include de l'application lorsqu'il est compilé.  
  
-   sqlncli11.lib  
  
     Doit être dans le chemin d'accès de la bibliothèque de l'éditeur de liens et spécifié comme fichier à lier. sqlncli11.lib est distribué avec le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
-   sqlncli11.dll  
  
     Doit être présent lors de l'exécution. sqlncli11.dll est distribué avec le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
> [!NOTE]  
>  ODBC **SQLBulkOperations** fonction n’a aucune relation avec la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des fonctions de copie en bloc. Les applications doivent utiliser les fonctions de copie en bloc spécifiques à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour effectuer les opérations de copie en bloc.  
  
## <a name="minimally-logging-bulk-copies"></a>Enregistrement minimal des copies en bloc dans le journal  
 Avec le mode de récupération complète, toutes les opérations d'insertion de lignes effectuées par le chargement en masse sont intégralement enregistrées dans le journal des transactions. Pour les chargements de données volumineux, le journal des transactions peut se remplir rapidement. Sous certaines conditions, l'enregistrement minimal est possible. L'enregistrement minimal réduit le risque qu'une opération de chargement en masse ne remplisse l'espace du journal et se révèle plus efficace que l'enregistrement complet.  
  
 Pour plus d’informations sur l’utilisation de la journalisation minimale, consultez [Prerequisites for Minimal Logging dans l’importation en bloc](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md).  
  
## <a name="remarks"></a>Notes  
 Lors de l'utilisation de bcp.exe dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure, il se peut que vous rencontriez des erreurs là où il n'en existait pas avant [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. La raison en est que dans les versions ultérieures, bcp.exe n'effectue plus la conversion implicite des types de données. Avant [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], bcp.exe convertissait les données numériques en type de données money, si la table cible avait un tel type. Toutefois, dans ce cas, bcp.exe tronquait simplement les champs supplémentaires. Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], quand les types de données ne correspondent pas entre le fichier et la table cible, bcp.exe déclenche une erreur s'il existe des données qui devraient être tronquées pour contenir dans la table cible. Pour résoudre cette erreur, corrigez les données de sorte qu'elles correspondent au type de données cible. Le cas échéant, utilisez bcp.exe à partir d'une version antérieure à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Utilisation de fichiers de données et de format](using-data-files-and-format-files.md)  
  
-   [Copie en bloc à partir de variables de programme](bulk-copying-from-program-variables.md)  
  
-   [Gestion des tailles de lot de copie en bloc](managing-bulk-copy-batch-sizes.md)  
  
-   [Copier en bloc des données texte et image](bulk-copying-text-and-image-data.md)  
  
-   [Conversion à partir de la bibliothèque de bases de données (DB-Library) vers une copie en bloc ODBC](converting-from-db-library-to-odbc-bulk-copy.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [Importation et exportation en bloc de données &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
