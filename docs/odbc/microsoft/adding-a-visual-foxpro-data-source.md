---
title: Ajout d’une source de données FoxPro visuelle (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1fd0c0f929ca00b7cf731dc92f07f69b6503f884
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307140"
---
# <a name="adding-a-visual-foxpro-data-source"></a>Ajout d’une source de données Visual FoxPro
Pour accéder aux données Visual FoxPro de votre application, vous devez disposer d’une source de données. Vous pouvez créer une source de données comme suit :  
  
-   Dans une application, comme Microsoft® Word, Microsoft Excel ou Microsoft Access, qui utilise des pilotes ODBC.  
  
-   En dehors de votre application, en utilisant le Microsoft Windows® 95, Microsoft Windows 98, ou Microsoft Windows NT®/Windows 2000 Control Panel.  
  
 Une fois qu’une source de données existe sur votre système, vous pouvez réutiliser la même source de données chaque fois que vous souhaitez accéder aux données Visual FoxPro. Si vous disposez de plusieurs bases de données ou de tableaux différents à laquelle vous souhaitez accéder, vous pouvez créer une source de données distincte pour chaque base de données ou répertoire.  
  
 La procédure suivante crée une source de données à l’aide de Control Panel. Pour plus d’informations sur la façon de créer une source de données à partir d’une application, voir [Accéder à visual FoxPro Data de Microsoft Office](../../odbc/microsoft/accessing-visual-foxpro-data-from-microsoft-office.md).  
  
### <a name="to-add-a-visual-foxpro-data-source"></a>Pour ajouter une source de données Visual FoxPro  
  
1.  Sur les ordinateurs qui exécutent Windows 2000, ouvrez le panneau de contrôle Windows et double clic outils administratifs.  
  
2.  Sources de données à double clic (ODBC) pour ouvrir la boîte de dialogue ODBC Data Source Administrator. Cette icône est disponible après avoir installé le Visual FoxPro ODBC Driver ou tout logiciel pilote ODBC.  
  
    > [!NOTE]  
    >  Si vous exécutez une version antérieure de Windows, ouvrez le panneau de contrôle Windows et double-cliquez 32 bits ODBC ou ODBC pour ouvrir la boîte de dialogue ODBC Data Source Administrator.  
  
3.  Cliquez sur Ajouter.  
  
4.  Dans la boîte de dialogue Create New Data Source, sélectionnez Microsoft Visual FoxPro Driver, puis cliquez sur Finition.  
  
5.  Dans la [boîte de dialogue ODBC Visual FoxPro Setup](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md), tapez le nom et la description de la source de données, sélectionnez le type de base de données, sélectionnez la base de données ou l’annuaire, puis cliquez sur OK.  
  
     Le nouveau nom source de données est affiché dans la liste des sources de données utilisateur dans l’onglet DSN utilisateur de la boîte de dialogue ODBC Data Source Administrator.  
  
6.  Cliquez sur OK pour enregistrer la nouvelle source de données et fermer la boîte de dialogue ODBC Data Source Administrator.
