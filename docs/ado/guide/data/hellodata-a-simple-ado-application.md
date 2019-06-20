---
title: 'HelloData : Une Application ADO Simple | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- HelloData sample application [ADO]
- ADO, samples
ms.assetid: de4bcd56-dac2-45e6-95ab-9fd7f25878fc
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 97957adf53cfea64693530b79920dd54d6d0a1bf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700635"
---
# <a name="hellodata-a-simple-ado-application"></a>HelloData : une application ADO simple
Les étapes de cette application simple à travers chacune des quatre principales opérations ADO : obtention, examen, la modification et la mise à jour des données. Ces opérations sont exécutées sur la base de données Northwind fournie avec Microsoft® SQL Server. Pour vous concentrer sur les notions de base d’ADO et éviter l’encombrement du code, la gestion des erreurs dans l’exemple est minime.  
  
### <a name="to-run-hellodata"></a>Pour exécuter HelloData  
  
1.  Créer un nouveau projet EXE Standard de Visual Basic qui fait référence à la bibliothèque ADO. Pour plus d’informations, consultez [référençant les bibliothèques ADO](../../../ado/guide/referencing-the-ado-libraries.md).  
  
2.  Créez quatre boutons de commande en haut du formulaire, en définissant le **nom** et **légende** propriétés avec les valeurs indiquées dans le tableau à la fin de cette rubrique.  
  
3.  Sous les boutons, ajoutez un **Microsoft contrôle DataGrid** (Msdatgrd.ocx). Ce fichier est inclus avec Visual Basic et se trouve dans votre répertoire \windows\system32 ou \winnt\system32. Pour ajouter le contrôle DataGrid à la boîte à outils Visual Basic, sélectionnez **composants...**  à partir de la **projet** menu. Puis la case à cocher à côté « Microsoft contrôle DataGrid 6.0 (SP3) (OLEDB) » puis cliquez sur **OK**. Pour ajouter le contrôle au projet, faites glisser le contrôle DataGrid de la boîte à outils vers le formulaire Visual Basic.  
  
4.  Créer un **zone de texte** sur le formulaire sous la grille et définissez ses propriétés comme indiqué dans le tableau. Le formulaire doit ressembler à la figure suivante lorsque vous avez terminé.  
  
5.  Pour finir, copiez le code répertorié dans [HelloData Code](../../../ado/guide/data/hellodata-code.md)et collez-le dans la fenêtre d’éditeur de code du formulaire. Appuyez sur **F5** pour exécuter le code.  
  
> [!NOTE]
>  Dans l’exemple suivant et dans ce guide, l’id d’utilisateur « MonID » avec un mot de passe de « 123aBc » est utilisé pour s’authentifier auprès du serveur. Vous devez remplacer ces valeurs avec les informations d’identification d’ouverture de session valide pour votre serveur. Remplacez également la valeur « MySQLServer » par le nom de votre serveur.  
  
 Pour obtenir une description détaillée du code, consultez [commentaires sur HelloData](../../../ado/guide/data/comments-on-hellodata.md).  
  
 ![Affiche le Formulaire1 de l’application HelloData VB](../../../ado/guide/data/media/hellodata.gif "HelloData")  
  
|Type de contrôle|Propriété|Value|  
|------------------|--------------|-----------|  
|Formulaire|Créer une vue d’abonnement|Form1|  
||Hauteur|6500|  
||Largeur|6500|  
|MS DataGrid|Créer une vue d’abonnement|grdDisplay1|  
|TextBox|Nom|txtDisplay1|  
||Multiligne|true|  
|Bouton de commande|Nom|cmdGetData|  
||Légende|Get Data|  
|Bouton de commande|Nom|cmdExamineData|  
||Légende|Examiner les données|  
|Bouton de commande|Nom|cmdEditData|  
||Légende|Modifier des données|  
|Bouton de commande|Nom|cmdUpdateData|  
||Légende|Données mises à jour|
