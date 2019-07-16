---
title: SET PATH, commande | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET PATH command [ODBC]
ms.assetid: db488d1e-0963-4f45-8c76-a23b9bde9e9d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 57685731bc5eb86381816d0cbb91a4942b5bfeff
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68063638"
---
# <a name="set-path-command"></a>SET PATH, commande
Spécifie un chemin d’accès pour les recherches de fichier. Pour plus d’informations spécifiques au pilote, consultez la section Notes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET PATH TO [Path]  
```  
  
## <a name="arguments"></a>Arguments  
 POUR [ *chemin d’accès*]  
 Spécifie les répertoires que vous souhaitez que Visual FoxPro à rechercher. Utilisez des virgules ou des points-virgules pour séparer les répertoires.  
  
## <a name="remarks"></a>Notes  
 DÉFINIR le chemin d’accès vous permet de spécifier des chemins de recherche pour d’autres programmes Visual FoxPro qui peuvent être appelées dans des procédures stockées. DÉFINIR le chemin d’accès ne changera pas le chemin d’accès de la source de données que vous avez spécifié pour la connexion.  
  
 Émettre définir les chemin d’accès à sans *chemin d’accès* pour restaurer le chemin d’accès au répertoire par défaut ou au dossier.  
  
## <a name="driver-remarks"></a>Notes de pilote  
 Si vous exécutez définir le chemin d’accès dans une procédure stockée, il sera ignoré par les commandes et les fonctions suivantes :  
  
-   Fonctions de catalogue comme [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md) et [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) ignore le nouveau chemin d’accès et continuer à référencer le chemin d’accès spécifié par la source de données dans [SQLPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md) ou [ SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
-   Commandes telles que SELECT, INSERT, UPDATE, DELETE et CREATE TABLE ignore le nouveau chemin d’accès et continuer à référencer le chemin d’accès spécifié par la source de données dans **SQLPrepare** ou **SQLExecDirect**.  
  
 Si vous émettez de définir le chemin d’accès dans une procédure stockée par la suite ne définissez pas le chemin d’accès à son état d’origine, les autres connexions à la base de données utilisera le nouveau chemin d’accès (étant donné que définir le chemin d’accès n’est pas étendue aux sessions de données).  
  
 Si vous souhaitez créer, sélectionner ou mettre à jour des tables dans un répertoire autre que celui spécifié par la source de données, spécifiez le chemin d’accès complet du fichier avec votre commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue d’installation ODBC Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)   
 [SQLColumns (pilote ODBC de Visual FoxPro)](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)   
 [SQLDriverConnect (pilote ODBC de Visual FoxPro)](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)   
 [SQLTables (pilote ODBC Visual FoxPro)](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)
