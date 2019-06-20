---
title: Ajout d’une Source de données Visual FoxPro | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro data source [ODBC], adding
- adding data sources [ODBC], Visual FoxPro ODBC driver
ms.assetid: 1487e188-52c8-4f48-b4fe-25a650dd9e97
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 262e8487e8133cf1c312659fa2fc28276aafa07e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63198278"
---
# <a name="adding-a-visual-foxpro-data-source"></a>Ajout d’une source de données Visual FoxPro
Pour accéder aux données Visual FoxPro à partir de votre application, vous devez disposer d’une source de données. Vous pouvez créer une source de données comme suit :  
  
-   Dans une application, comme Microsoft® Word, Microsoft Excel ou Microsoft Access, qui utilise des pilotes ODBC.  
  
-   En dehors de votre application, à l’aide de la Microsoft Windows® 95, Microsoft Windows 98 ou Microsoft Windows/Windows 2000 le panneau de configuration.  
  
 Une fois une source de données existe sur votre système, vous pouvez réutiliser la même source de données chaque fois que vous souhaitez accéder aux données Visual FoxPro. Si vous avez plusieurs bases de données différentes ou les tables que vous souhaitez accéder, vous pouvez créer une source de données distincte pour chaque base de données ou un répertoire.  
  
 La procédure suivante crée une source de données en utilisant le panneau de configuration. Pour plus d’informations sur la création d’une source de données à partir d’une application, consultez [l’accès aux données à partir de Microsoft Office](../../odbc/microsoft/accessing-visual-foxpro-data-from-microsoft-office.md).  
  
### <a name="to-add-a-visual-foxpro-data-source"></a>Pour ajouter une source de données Visual FoxPro  
  
1.  Sur les ordinateurs qui exécutent Windows 2000, ouvrez le panneau de configuration Windows et double-cliquez sur Outils d’administration.  
  
2.  Double-cliquez sur Sources de données (ODBC) pour ouvrir la boîte de dialogue Administrateur de sources de données ODBC. Cette icône est disponible une fois que vous avez installé le pilote ODBC Visual FoxPro ou n’importe quel logiciel de pilote ODBC.  
  
    > [!NOTE]  
    >  Si vous exécutez une version antérieure de Windows, ouvrez le panneau de configuration Windows et double-cliquez sur 32 bits ODBC ou ODBC pour ouvrir la boîte de dialogue Administrateur de sources de données ODBC.  
  
3.  Cliquez sur Ajouter.  
  
4.  Dans la boîte de dialogue Créer une nouvelle Source de données, sélectionnez le pilote Microsoft Visual FoxPro et puis cliquez sur Terminer.  
  
5.  Dans le [boîte de dialogue d’installation de ODBC Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md), tapez le nom de source de données et la description, sélectionnez le type de base de données, sélectionnez la base de données ou un répertoire, puis cliquez sur OK.  
  
     Le nouveau nom de source de données s’affiche dans la liste de Sources de données utilisateur dans l’onglet DSN utilisateur de la boîte de dialogue Administrateur de sources de données ODBC.  
  
6.  Cliquez sur OK pour enregistrer la nouvelle source de données et de fermer la boîte de dialogue Administrateur de sources de données ODBC.
