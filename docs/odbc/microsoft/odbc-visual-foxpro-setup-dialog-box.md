---
title: ODBC Visual FoxPro Setup Dialog Box (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], installing
- FoxPro ODBC driver [ODBC], installing
ms.assetid: de020197-7f53-4643-9cbf-b7887ba88de9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ef7ac702a69342833c6dfffa0ffc9cdd0ac2857e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298079"
---
# <a name="odbc-visual-foxpro-setup-dialog-box"></a>Configuration d’ODBC pour Visual FoxPro, boîte de dialogue
La boîte de dialogue **ODBC Visual FoxPro Setup** vous permet d’ajouter ou de modifier une source de données Visual FoxPro.  
  
 Pour télécharger le pilote, consultez [le site de téléchargement Visual FoxPro ODBC Driver](https://go.microsoft.com/fwlink/?LinkId=121318).  
  
## <a name="dialog-box-options"></a>Options de boîte de dialogue  
 **Nom de source de données**  
 Tapez le nom que vous souhaitez utiliser pour la source de données.  
  
 **Description**  
 Tapez une description pour la source de données.  
  
 **Type de base de données**  
 Vous permet de choisir le type de base de données vers lequel vous souhaitez que votre source de données se connecte.  
  
 **Base de données Visuelle FoxPro (. DBC)**  
 Précise que la source de données se connecte à une [base de données](../../odbc/microsoft/visual-foxpro-terminology.md) Visual FoxPro (.dbc fichier) et à toutes les tables et vues locales dans la base de données.  
  
 **Annuaire de la Table Libre**  
 Précise que la source de données se connecte à un répertoire de [tables gratuites](../../odbc/microsoft/visual-foxpro-terminology.md). Toutes les tables [de base de données](../../odbc/microsoft/visual-foxpro-terminology.md) dans le même répertoire sont ignorées par les fonctions de catalogue ODBC telles que [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) ou [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md). Les tables de base de données peuvent être consultées en utilisant les instructions SQL SELECT envoyées par [SQLExecute](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md) et [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
 **Chemin d’accès**  
 Affiche le chemin et le nom de la base de données ou l’annuaire des tables gratuites auxquelles la source de données se connecte.  
  
 **Parcourir**  
 Vous permet de rechercher votre système et votre réseau pour la base de données ou l’annuaire auquel vous souhaitez connecter la source de données.  
  
 **Options**  
 Élargit la boîte de dialogue afin que vous puissiez définir les options Visual FoxPro ODBC Driver.  
  
## <a name="driver"></a>Pilote  
 **Séquence de collation**  
 La séquence dans laquelle les champs sont triés. Les séquences par défaut reflètent les séquences prises en charge par votre version linguistique du système d’exploitation. Pour une liste de séquences de collation prises en charge, voir [SET COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
 **Exclusive**  
 Lorsque cette case à cocher est sélectionnée, le pilote ouvre la base de données Visual FoxPro exclusivement lorsque vous accédez aux données à l’aide de la source de données. D’autres utilisateurs ne peuvent pas accéder à la base de données ou aux tables de la base de données pendant que la base de données est ouverte exclusivement. Les tables dans la base de données exclusivement ouverte sont ouvertes en tant que SHARED. Pour ouvrir une table exclusivement, utilisez la commande [SET EXCLUSIVE.](../../odbc/microsoft/set-exclusive-command.md) Cette case à cocher est désactivée lorsque **le type de base de données** est réglé sur le répertoire de la Table **Libre.**  
  
 **Null**  
 Détermine si les colonnes créées avec ALTER TABLE et CREATE TABLE permettent des valeurs nulles. Si vous définissez Null ON, INSERT - SQL insère une valeur nulle dans n’importe quelle colonne non incluse dans un INSERT - SQL... Clause VALUE. Un blanc est inséré si Null est OFF. Vous pouvez également contrôler cette option via une chaîne de connexion passée comme dans le code suivant :  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;NULL=NO"  
```  
  
 **Deleted**  
 Détermine si les lignes marquées comme supprimées sont retournées. Vous pouvez également contrôler cette option via une chaîne de connexion passée comme dans le code suivant :  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;  
DELETED=YES"  
```  
  
 **Aller chercher des données en arrière-plan**  
 Détermine si les enregistrements seront récupérés en arrière-plan (aller chercher progressif) ou si votre demande attendra que tous les enregistrements de l’ensemble de résultats soient récupérés.
