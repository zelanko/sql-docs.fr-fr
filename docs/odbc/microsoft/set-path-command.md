---
title: Set PATH Commande (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e44093c3ea18bc995264a8974726f5af0abe3b3a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300819"
---
# <a name="set-path-command"></a>SET PATH, commande
Spécifie un chemin pour les recherches de fichiers. Pour obtenir des renseignements spécifiques au conducteur, consultez les remarques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET PATH TO [Path]  
```  
  
## <a name="arguments"></a>Arguments  
 À *[Chemin*]  
 Spécifie les répertoires que vous souhaitez visual FoxPro à rechercher. Utilisez des virgules ou des semi-colons pour séparer les répertoires.  
  
## <a name="remarks"></a>Notes  
 SET PATH vous permet de spécifier les voies de recherche d’autres programmes Visual FoxPro qui peuvent être appelés dans les procédures stockées. SET PATH ne modifiera pas la trajectoire de la source de données que vous avez spécifiée pour la connexion.  
  
 Question SET PATH TO sans *Chemin* pour restaurer le chemin vers l’annuaire par défaut ou le dossier.  
  
## <a name="driver-remarks"></a>Remarques du conducteur  
 Si vous émetssez SET PATH dans une procédure stockée, il sera ignoré par les fonctions et les commandes suivantes :  
  
-   Les fonctions de catalogue telles que [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md) et [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) ignoreront la nouvelle voie et continueront de faire référence au chemin spécifié par la source de données dans [SQLPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md) ou [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
-   Des commandes telles que SELECT, INSERT, UPDATE, DELETE et CREATE TABLE ignoreront la nouvelle voie et continueront de faire référence au chemin spécifié par la source de données dans **SQLPrepare** ou **SQLExecDirect**.  
  
 Si vous publiez SET PATH dans une procédure stockée et que vous ne réglez pas par la suite le chemin du retour à son état d’origine, d’autres connexions à la base de données utiliseront la nouvelle voie (parce que SET PATH n’est pas étendue aux sessions de données).  
  
 Si vous souhaitez créer, sélectionner ou mettre à jour des tables dans un répertoire autre que celui spécifié par la source de données, spécifiez la trajectoire complète du fichier avec votre commande.  
  
## <a name="see-also"></a>Voir aussi  
 [ODBC Visual FoxPro Setup Dialog Box](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)   
 [SQLColumns (Visual FoxPro ODBC Driver)](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)   
 [SQLDriverConnect (Visual FoxPro ODBC Driver)](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)   
 [SQLTables (pilote ODBC Visual FoxPro)](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)
