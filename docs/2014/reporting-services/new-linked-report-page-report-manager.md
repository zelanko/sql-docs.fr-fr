---
title: Page nouveau rapport lié (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: fefb46e8-6901-4d50-a3f8-7c49ad72e7b1
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: baca8a9c339ff55ad25f390ac73a2957fdd26447
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48119369"
---
# <a name="new-linked-report-page-report-manager"></a>Page Nouveau rapport lié (Gestionnaire de rapports)
  La page Nouveau rapport lié vous permet de créer un rapport lié. Un rapport lié est un rapport qui possède ses propres paramètres et propriétés, mais qui est lié à la définition de rapport d'un autre rapport. Les rapports liés sont utiles lorsque vous possédez un rapport de base que vous souhaitez modifier pour des groupes ou des utilisateurs spécifiques (par exemple, un rapport régional qui retourne des données différentes selon le code de région que vous spécifiez en tant que paramètre). Un rapport lié est généralement créé à partir d'un rapport paramétrable lorsque vous souhaitez modifier puis enregistrer des valeurs de paramètres différentes avec chaque instance du rapport. Toutefois, vous pouvez créer un rapport lié à partir de n'importe quel rapport auquel vous avez accès.  
  
 Un rapport lié peut posséder son nom, sa description, son emplacement, ses propriétés de paramètres, ses propriétés d'exécution de rapport, ses propriétés d'historique de rapport, ses autorisations et ses abonnements propres. Toutefois, un rapport lié doit utiliser les propriétés de source de données et la mise en page du rapport de base qui fournit la définition de rapport.  
  
## <a name="navigation"></a>Navigation  
 Utilisez les procédures suivantes pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-new-linked-report-page-from-the-contents-page"></a>Pour ouvrir la page Nouveau rapport lié depuis la page Contenu  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez un rapport pour lequel vous souhaitez créer un rapport lié.  
  
2.  Pointez sur le rapport et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Créer un rapport lié**.  
  
###### <a name="to-open-the-new-linked-report-page-from-the-general-properties-page-of-a-report"></a>Pour ouvrir la page Nouveau rapport lié dans la page des propriétés générales d'un rapport  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez un rapport pour lequel vous souhaitez créer un rapport lié.  
  
2.  Pointez sur le rapport et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Gérer**. La page des propriétés générales pour le rapport s'ouvre.  
  
4.  Dans la barre d'outils de l'élément, cliquez sur **Créer un rapport lié**.  
  
## <a name="options"></a>Options  
 **Nom**  
 Spécifie le nom du rapport lié. Le nom doit contenir un caractère alphanumérique au minimum. Il peut également comporter des espaces et certains symboles. Toutefois, vous ne devez pas utiliser les caractères ; ? : \@ & = +, $ / * \< > | "ou / lorsque vous spécifiez un nom.  
  
 **Description**  
 Tapez une description du contenu du rapport. Cette description apparaît dans la page Contenu. Elle est visible par les utilisateurs qui sont autorisés à accéder au rapport.  
  
 **Emplacement**  
 Spécifie le chemin d'accès au dossier qui contient le rapport. Par défaut, les rapports liés sont créés comme des frères du rapport de base. Cliquez sur **Modifier l'emplacement** pour placer le rapport lié dans un autre dossier.  
  
 **OK**  
 Cliquez sur **OK** pour enregistrer vos modifications et retourner à la page des propriétés générales du rapport de base.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un rapport lié](reports/create-a-linked-report.md)   
 [Page Propriétés générales, Rapports &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md)   
 [Aide (F1) du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
