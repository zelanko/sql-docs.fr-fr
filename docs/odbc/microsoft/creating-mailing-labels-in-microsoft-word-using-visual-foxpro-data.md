---
title: Création d’étiquettes postales dans microsoft Word à l’aide de données Visuelles FoxPro (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro data [ODBC], mailing labels
- Visual FoxPro data [ODBC], Word
- mailing labels [ODBC]
- Visual FoxPro ODBC driver [ODBC], Word
- FoxPro ODBC driver [ODBC], word
ms.assetid: c901b60c-9f84-407a-b3d1-b4d301a71370
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c3ca6c729cfa988e2560192d705bc24e9e7b4fa1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280799"
---
# <a name="creating-mailing-labels-in-microsoft-word-using-visual-foxpro-data"></a>Création d’étiquettes de publipostage dans Microsoft Word avec des données Visual FoxPro
Vous pouvez utiliser les données Visual FoxPro dans un document Microsoft Word pour Windows 95 ou Windows 98. Par exemple, vous pouvez créer des étiquettes de diffusion à partir des informations client stockées dans une table Visual FoxPro.  
  
### <a name="to-create-mailing-labels"></a>Créer des étiquettes d’envoi  
  
1.  Dans Microsoft Word, créez un nouveau document vierge.  
  
2.  Dans le menu Tools, choisissez Mail Merge.  
  
3.  Dans l’aide à la fusion de courrier, choisissez Créer et sélectionnez ensuite les étiquettes de diffusion.  
  
4.  Sous document principal, choisissez Active Window.  
  
5.  Sous Source de données, choisissez Get Data et sélectionnez La source de données ouvertes.  
  
6.  Dans la boîte de dialogue Open Data Source, choisissez MS Query.  
  
7.  Dans la boîte de dialogue Select Data Source, sélectionnez une source de données Visual FoxPro, puis cliquez sur Use.  
  
8.  Si la base de données consultée par votre source de données comprend des tables, sélectionnez une table à partir de la boîte de dialogue Add Tables. Microsoft Query affiche la table ajoutée dans la moitié supérieure du concepteur de requêtes.  
  
9. Sélectionnez les champs pour votre requête en les faisant glisser de la table sur la moitié inférieure du concepteur.  
  
10. Du menu Fichier, choisissez Return Data à Microsoft Word. Microsoft Query ferme, et les données que vous avez sélectionnées sont disponibles pour une utilisation dans votre document de fusion de courrier.  
  
11. Sous document principal, choisissez Setup.  
  
12. Dans la boîte de dialogue Label Options, sélectionnez les informations d’imprimante et d’étiquetage que vous voulez, puis cliquez sur OK.  
  
13. Dans la boîte de dialogue Create Labels, sélectionnez les champs que vous souhaitez imprimer sur les étiquettes d’envoi, puis cliquez sur OK.  
  
14. Dans l’aide à la fusion de courrier, dans le cadre de la fusion des données avec le document, cliquez sur Fusion.  
  
15. Dans la boîte de dialogue De fusion, sélectionnez les options que vous voulez, puis cliquez sur Merge.
