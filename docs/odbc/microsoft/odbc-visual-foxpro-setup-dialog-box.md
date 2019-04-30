---
title: Boîte de dialogue d’installation ODBC Visual FoxPro | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 35e9da17a9c3980470cfd3dcbb22b4069afec640
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63233586"
---
# <a name="odbc-visual-foxpro-setup-dialog-box"></a>Configuration d’ODBC pour Visual FoxPro, boîte de dialogue
Le **d’installation de ODBC Visual FoxPro** boîte de dialogue vous permet d’ajouter ou modifier une source de données Visual FoxPro.  
  
 Pour télécharger le pilote, consultez [le site de téléchargement du pilote ODBC Visual FoxPro](https://go.microsoft.com/fwlink/?LinkId=121318).  
  
## <a name="dialog-box-options"></a>Options de boîte de dialogue  
 **Nom de Source de données**  
 Tapez le nom que vous souhaitez utiliser pour la source de données.  
  
 **Description**  
 Tapez une description pour la source de données.  
  
 **Type de base de données**  
 Vous permet de choisir le type de base de données pour se connecter à votre source de données.  
  
 **Base de données Visual FoxPro (. DBC)**  
 Spécifie que la source de données se connecte à un Visual FoxPro [base de données](../../odbc/microsoft/visual-foxpro-terminology.md) (fichier .dbc) et à toutes les tables et vues locales dans la base de données.  
  
 **Répertoire de Table libre**  
 Spécifie que la source de données se connecte à un répertoire de [gratuit tables](../../odbc/microsoft/visual-foxpro-terminology.md). N’importe quel [base de données](../../odbc/microsoft/visual-foxpro-terminology.md) tables dans le même répertoire sont ignorés par les fonctions de catalogue ODBC comme [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) ou [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md). Tables de base de données est accessible à l’aide d’instructions SQL SELECT envoyées via [SQLExecute](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md) et [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
 **Chemin d'accès**  
 Affiche le chemin d’accès et le nom de la base de données ou le répertoire de tables indépendantes à laquelle la source de données se connecte.  
  
 **Parcourir**  
 Vous permet de rechercher votre système et votre réseau pour la base de données ou le répertoire auquel vous souhaitez vous connecter la source de données.  
  
 **Options**  
 Développe la boîte de dialogue afin que vous pouvez définir les options de pilote ODBC Visual FoxPro.  
  
## <a name="driver"></a>Pilote  
 **Séquence de classement**  
 La séquence dans laquelle les champs sont triés. Les séquences par défaut reflètent les séquences pris en charge par votre version de langue du système d’exploitation. Pour obtenir la liste de séquences de classement pris en charge, consultez [définir COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
 **Exclusive**  
 Lorsque cette case à cocher est sélectionnée, le pilote s’ouvre à la base de données Visual FoxPro exclusivement lorsque vous accédez aux données à l’aide de la source de données. Autres utilisateurs ne peuvent pas accéder à la base de données ou les tables dans la base de données pendant que la base de données est ouverte en mode exclusif. Tables au sein de la base de données exclusivement ouvert sont ouverts en tant que partagé. Pour ouvrir une table exclusivement, utilisez le [définir exclusif](../../odbc/microsoft/set-exclusive-command.md) commande. Cette case à cocher est désactivée lorsque **type base de données** a la valeur **Free Table directory**.  
  
 **Null**  
 Détermine si les colonnes créées avec ALTER TABLE et CREATE TABLE autorisent les valeurs null. Si vous définissez sur Null, insertion - SQL insère une valeur null dans n’importe quelle colonne ne pas incluse dans une instruction INSERT - SQL... Clause de valeur. Une valeur vide est insérée si Null est désactivée (OFF). Vous pouvez également contrôler cette option dans une chaîne de connexion passée comme dans le code suivant :  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;NULL=NO"  
```  
  
 **Deleted**  
 Détermine si les lignes marquées comme supprimées sont retournées. Vous pouvez également contrôler cette option dans une chaîne de connexion passée comme dans le code suivant :  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;  
DELETED=YES"  
```  
  
 **Extraire les données en arrière-plan**  
 Détermine si les enregistrements seront extraits en arrière-plan (extraction progressif) ou votre application attend que tous les enregistrements du jeu de résultats sont extraites.
