---
title: Ajout d’une source de données Visual FoxPro | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307140"
---
# <a name="adding-a-visual-foxpro-data-source"></a>Ajout d’une source de données Visual FoxPro
Pour accéder aux données Visual FoxPro à partir de votre application, vous devez disposer d’une source de données. Vous pouvez créer une source de données comme suit :  
  
-   Dans une application, telle que Microsoft® Word, Microsoft Excel ou Microsoft Access, qui utilise des pilotes ODBC.  
  
-   En dehors de votre application, à l’aide du panneau de configuration Microsoft Windows® 95, Microsoft Windows 98 ou Microsoft Windows NT®/Windows 2000.  
  
 Une fois qu’une source de données existe sur votre système, vous pouvez réutiliser la même source de données chaque fois que vous souhaitez accéder aux données Visual FoxPro. Si vous avez plusieurs bases de données ou tables auxquelles vous souhaitez accéder, vous pouvez créer une source de données distincte pour chaque base de données ou répertoire.  
  
 La procédure suivante crée une source de données à l’aide du panneau de configuration. Pour plus d’informations sur la création d’une source de données à partir d’une application, consultez [accès aux données Visual FoxPro à partir de Microsoft Office](../../odbc/microsoft/accessing-visual-foxpro-data-from-microsoft-office.md).  
  
### <a name="to-add-a-visual-foxpro-data-source"></a>Pour ajouter une source de données Visual FoxPro  
  
1.  Sur les ordinateurs qui exécutent Windows 2000, ouvrez le panneau de configuration Windows et double-cliquez sur outils d’administration.  
  
2.  Double-cliquez sur sources de données (ODBC) pour ouvrir la boîte de dialogue administrateur de sources de données ODBC. Cette icône est disponible après l’installation du pilote ODBC Visual FoxPro ou de tout logiciel de pilote ODBC.  
  
    > [!NOTE]  
    >  Si vous exécutez une version antérieure de Windows, ouvrez le panneau de configuration Windows et double-cliquez sur ODBC ou ODBC 32 bits pour ouvrir la boîte de dialogue administrateur de sources de données ODBC.  
  
3.  Cliquez sur Ajouter.  
  
4.  Dans la boîte de dialogue créer une nouvelle source de données, sélectionnez pilote Microsoft Visual FoxPro, puis cliquez sur Terminer.  
  
5.  Dans la [boîte de dialogue installation de ODBC pour Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md), tapez le nom et la description de la source de données, sélectionnez le type de base de données, sélectionnez la base de données ou le répertoire, puis cliquez sur OK.  
  
     Le nouveau nom de source de données s’affiche dans la liste sources de données utilisateur sous l’onglet DSN utilisateur de la boîte de dialogue administrateur de sources de données ODBC.  
  
6.  Cliquez sur OK pour enregistrer la nouvelle source de données et fermer la boîte de dialogue administrateur de la source de données ODBC.
