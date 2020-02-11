---
title: Boîte de dialogue installation de ODBC pour Visual FoxPro | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d9aa8954cd42ac715b3e6e67e0b0add69d07a570
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915663"
---
# <a name="odbc-visual-foxpro-setup-dialog-box"></a>Configuration d’ODBC pour Visual FoxPro, boîte de dialogue
La boîte de dialogue **installation de ODBC Visual FoxPro** vous permet d’ajouter ou de modifier une source de données Visual FoxPro.  
  
 Pour télécharger le pilote, consultez [le site de téléchargement du pilote ODBC Visual FoxPro](https://go.microsoft.com/fwlink/?LinkId=121318).  
  
## <a name="dialog-box-options"></a>Options de boîte de dialogue  
 **Nom de la source de données**  
 Tapez le nom que vous souhaitez utiliser pour la source de données.  
  
 **Description**  
 Tapez une description de la source de données.  
  
 **Type de base de données**  
 Vous permet de choisir le type de base de données à laquelle vous souhaitez que votre source de données se connecte.  
  
 **Base de données Visual FoxPro (. BC**  
 Spécifie que la source de données se connecte à une [base de](../../odbc/microsoft/visual-foxpro-terminology.md) données Visual FoxPro (fichier. DBC) et à toutes les tables et vues locales de la base de données.  
  
 **Répertoire de table libre**  
 Spécifie que la source de données se connecte à un répertoire de [tables libres](../../odbc/microsoft/visual-foxpro-terminology.md). Toutes les tables [de base de données](../../odbc/microsoft/visual-foxpro-terminology.md) dans le même répertoire sont ignorées par les fonctions de catalogue ODBC telles que [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) ou [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md). Les tables de base de données sont accessibles à l’aide d’instructions SQL SELECT envoyées via [SQLExecute](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md) et [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
 **Chemin d’accès**  
 Affiche le chemin d’accès et le nom de la base de données ou le répertoire des tables libres auxquelles la source de données se connecte.  
  
 **Parcourir**  
 Vous permet de rechercher dans votre système et votre réseau la base de données ou le répertoire auquel vous souhaitez connecter la source de données.  
  
 **Options**  
 Développe la boîte de dialogue pour vous permettre de définir les options du pilote ODBC Visual FoxPro.  
  
## <a name="driver"></a>Pilote  
 **Séquence de classement**  
 Séquence dans laquelle les champs sont triés. Les séquences par défaut reflètent les séquences prises en charge par votre version linguistique du système d’exploitation. Pour obtenir la liste des séquences de classement prises en charge, consultez [Set COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
 **Exclusif**  
 Lorsque cette case à cocher est activée, le pilote ouvre la base de données Visual FoxPro exclusivement lorsque vous accédez aux données à l’aide de la source de données. Les autres utilisateurs ne peuvent pas accéder à la base de données ou aux tables de la base de données pendant que la base de données est ouverte en mode exclusif. Les tables de la base de données exclusivement ouverte sont ouvertes en tant que données PARTAGÉes. Pour ouvrir une table en mode exclusif, utilisez la commande [Set exclusive](../../odbc/microsoft/set-exclusive-command.md) . Cette case à cocher est désactivée lorsque le **type de base de données** est défini sur **Répertoire de table libre**.  
  
 **Null**  
 Détermine si les colonnes créées avec ALTER TABLE et CREATE TABLE autorisent les valeurs NULL. Si vous définissez la valeur NULL sur, INSERT-SQL insère une valeur null dans une colonne qui n’est pas incluse dans un INSERT-SQL... Clause VALUE. Un espace est inséré si null est désactivé. Vous pouvez également contrôler cette option via une chaîne de connexion passée, comme dans le code suivant :  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;NULL=NO"  
```  
  
 **Supprimé**  
 Détermine si les lignes marquées comme supprimées sont retournées. Vous pouvez également contrôler cette option via une chaîne de connexion passée, comme dans le code suivant :  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;  
DELETED=YES"  
```  
  
 **Récupérer des données en arrière-plan**  
 Détermine si les enregistrements sont extraits en arrière-plan (extraction progressive) ou si votre application attend que tous les enregistrements du jeu de résultats soient extraits.
