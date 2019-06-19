---
title: Création d’étiquettes de publipostage dans Microsoft Word à l’aide de données Visual FoxPro | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2c759e530baf792de7e015eac87337f35cf9f5a1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63312536"
---
# <a name="creating-mailing-labels-in-microsoft-word-using-visual-foxpro-data"></a>Création d’étiquettes de publipostage dans Microsoft Word avec des données Visual FoxPro
Vous pouvez utiliser des données Visual FoxPro dans Microsoft Word pour Windows 95 ou Windows 98 document. Par exemple, vous souhaiterez peut-être créer des étiquettes de publipostage à partir des informations client stockées dans une table Visual FoxPro.  
  
### <a name="to-create-mailing-labels"></a>Pour créer des étiquettes de publipostage  
  
1.  Dans Microsoft Word, créez un nouveau document vierge.  
  
2.  Dans le menu Outils, choisissez le publipostage.  
  
3.  Dans l’application auxiliaire de publipostage, sélectionnez Créer, puis sélectionnez les étiquettes de publipostage.  
  
4.  Sous Document principal, choisissez la fenêtre Active.  
  
5.  Sous la Source de données, choisissez d’obtenir des données, puis sélectionnez Open Source de données.  
  
6.  Dans la boîte de dialogue Open Source de données, choisissez MS Query.  
  
7.  Dans la boîte de dialogue Sélectionner une Source de données, sélectionnez une source de données Visual FoxPro, puis sur utilisation.  
  
8.  Si la base de données accédé par votre source de données comprend des tables, sélectionnez une table dans la boîte de dialogue Ajouter des Tables. Microsoft Query affiche la table ajoutée dans la partie supérieure du Concepteur de requêtes.  
  
9. Sélectionnez les champs de votre requête en les faisant glisser à partir de la table vers le bas la moitié du concepteur.  
  
10. Dans le menu fichier, choisissez renvoyer des données vers Microsoft Word. Microsoft Query se ferme et les données que vous avez sélectionné ne seront disponibles pour une utilisation dans votre document de fusion.  
  
11. Sous Document principal, choisissez le programme d’installation.  
  
12. Dans la boîte de dialogue Options d’étiquette, sélectionnez les informations de l’imprimante et étiquette puis cliquez sur OK.  
  
13. Dans la boîte de dialogue Créer des étiquettes, sélectionnez les champs que vous souhaitez imprimer sur les étiquettes de publipostage, puis cliquez sur OK.  
  
14. Dans l’application auxiliaire de fusion et publipostage, sous la fusionner les données avec le Document, cliquez sur Fusionner.  
  
15. Dans la boîte de dialogue de fusion, sélectionnez les options souhaitées, puis cliquez sur Fusionner.
