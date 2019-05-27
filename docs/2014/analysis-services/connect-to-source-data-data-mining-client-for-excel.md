---
title: Se connecter à la Source de données (Client d’exploration de données pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- connections
ms.assetid: 548672ce-e403-4aca-b67a-c2c797f053dd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 468686314bb2446415a6883c6233708f9cbd1d2b
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66087099"
---
# <a name="connect-to-source-data-data-mining-client-for-excel"></a>Connexion à une source de données (Client d'exploration de données pour Excel)
  Cette rubrique décrit comment créer et utiliser les connexions utilisées pour stocker des modèles d'exploration de données et pour accéder aux données externes stockées dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 **Connexions d’exploration de données.** La connexion initiale que vous créez lorsque vous lancez les compléments permet d'accéder aux algorithmes, d'analyser les données et de stocker les modèles et structures d'exploration de données.  
  
 Une connexion à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] est nécessaire pour utiliser les outils de modélisation et de visualisation des compléments, car ces derniers dépendent d'algorithmes et de structures de données qui sont fournis par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 **Connexions aux sources de données externes.** Vous pouvez également créer des connexions à des données externes lorsque vous créez des modèles ou enregistrez les résultats. Par exemple, vous pouvez créer un modèle d'exploration de données sur un serveur, puis exécuter une requête de prédiction par rapport au modèle d'exploration de données à l'aide de données stockées dans une autre instance d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], dans un tableau de données Excel, ou dans une source de données externes telle que [!INCLUDE[msCoName](../includes/msconame-md.md)] Access. À chaque fois que vous accédez à une nouvelle source de données, le système vous demande de créer une connexion à l'aide d'une boîte de dialogue.  
  
##  <a name="bkmk_prereq2"></a> Conditions préalables  
 Cette version des compléments nécessite que votre instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] soit SQL Server 2012. Une version séparée des compléments est disponible si vous souhaitez vous connecter à une version antérieure d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Il existe des versions des compléments qui prennent en charge SQL Server 2005, SQL Server 2008 et SQL Server 2008 R2.  
  
 Pour vous connecter à une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], vous devez disposer des autorisations d'accès au serveur de base de données. De plus, les sessions d'exploration de données doivent être activées, et vous devez disposer des autorisations de lecture ou de lecture/écriture sur des objets de base de données stockés sur le serveur.  
  
##  <a name="bkmk_connect"></a> Création de connexions au serveur d’exploration de données  
 Le **connexions** groupe dans le Client d’exploration de données pour Excel et les outils d’analyse de Table pour Excel fournit des outils pour gérer les connexions à une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
-   Vous pouvez créer la connexion lorsque vous installez le complément, ou vous pouvez ajouter une connexion par la suite.  
  
-   Vous pouvez créer plusieurs connexions et les modifier à tout moment, sauf si vous est en train de créer ou d'interroger un modèle.  
  
     Ne modifiez pas ou ne désactivez pas une connexion lors du traitement d'un modèle d'exploration de données. Le modèle d'exploration de données peut perdre des données ou devenir inutilisable.  
  
-   Une seule connexion peut être active à un moment donné.  
  
### <a name="connections-in-the-excel-add-ins"></a>Connexions dans les compléments Excel  
 Le **connexions** groupe dans le Client d’exploration de données pour Excel et les outils d’analyse de Table pour Excel est la gestion des connexions à une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
##### <a name="create-a-new-server-connection-in-the-excel-add-ins"></a>Créer une nouvelle connexion au serveur dans les compléments Excel  
  
1.  Cliquez sur le **connexion** bouton sur le **analyser** ou **d’exploration de données** ruban.  
  
    > [!NOTE]  
    >  Le texte du bouton indique si une connexion existe. Lorsqu’aucune connexion n’a été apportée dans la feuille de calcul, le bouton contient le texte «\<aucune connexion >. » Si une connexion a été établie auparavant dans la feuille de calcul, le nom de cette connexion s'affiche sur le bouton.  
  
2.  Dans le **connexions Analysis Services** boîte de dialogue, cliquez sur **New**.  
  
3.  Dans le **nouvelle connexion Analysis Services** boîte de dialogue, tapez le nom du serveur.  
  
4.  Spécifiez la méthode d'authentification.  
  
5.  Sélectionnez une base de données à partir de la **nom de catalogue** liste déroulante. Si aucune base de données n’existe sur l’instance, sélectionnez **(valeur par défaut)**.  
  
6.  Tapez un nom convivial pour la connexion.  
  
7.  Cliquez sur **tester la connexion** pour vérifier que le serveur et la base de données sont disponibles.  
  
8.  Cliquez sur **OK**, puis sur **Fermer**.  
  
### <a name="connections-using-a-web-service"></a>Connexions à l'aide d'un service Web  
 Si vous utilisez une architecture de client léger pour permettre l’exploration de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cubes et des données, vous pouvez également configurer une connexion à un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server via les services Web. Pour obtenir des informations sur la manière de définir un client Web, consultez la documentation en ligne de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Si vous avez accès à un serveur qui a été configuré pour des services Web, vous pouvez spécifier le type de connexion lorsque vous créez celle-ci pour la première fois.  
  
##### <a name="create-an-http-connection-to-analysis-services"></a>Créer une connexion HTTP à Analysis Services  
  
1.  Ouvrez le **nouvelle connexion Analysis Services** boîte de dialogue.  
  
2.  Pour le nom du serveur, tapez http:// suivi de l'URL affecté au serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
3.  Tapez le nom d'utilisateur et le mot de passe qui sont nécessaires pour accéder au service Web.  
  
### <a name="connections-in-the-visio-add-in"></a>Connexions dans le complément Visio  
 Contrairement à Excel, Visio ne fournit pas un ruban outil et il n'y a pas de boutons destinés à la création ou au contrôle des connexions. En revanche, la connexion de données est créée lorsque vous choisissez une forme d'exploration de données pour la première fois et que vous la déposez sur une page Visio. Un Assistant vous invitera à sélectionner le modèle pour la forme et à définir d'autres options.  
  
 Si vous avez utilisé précédemment une connexion à un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] de source de données dans Excel, ces connexions sont répertoriées en tant que sources de données possibles à partir de laquelle sélectionner.  
  
##### <a name="create-a-connection-for-a-visio-shape"></a>Créer une connexion pour une forme Visio  
  
1.  Ouvrez le modèle d'exploration de données et sélectionnez une des formes d'exploration de données.  
  
2.  Effectuez un glisser-déplacer de la forme vers une page vide.  
  
3.  Dans le **sélectionner une source de données** boîte de dialogue, sélectionnez une données source à partir de la liste ou cliquez sur **New**.  
  
4.  Si vous sélectionnez **New**, suivez la procédure décrite précédemment pour spécifier un nom de catalogue et le serveur, ou pour vous connecter via un service Web.  
  
##  <a name="bkmk_change"></a> Modification des connexions  
 Vous pouvez créer plusieurs connexions dans la même feuille de calcul mais une seule connexion peut être active à la fois. Le nom de la connexion actuelle est affiché dans le **connexion** bouton.  
  
 Dans le Client d’exploration de données pour Excel, vous pouvez également vérifier la chaîne de connexion et l’état de la connexion actuelle en cliquant sur **Trace** , puis en cliquant sur **connexion actuelle**.  
  
#### <a name="use-a-different-server-connection"></a>Utiliser une connexion différente à un serveur  
  
1.  Cliquez sur **connexion**.  
  
2.  Dans le **connexions Analysis Services** volet, sélectionnez une connexion à partir de la **autres connexions** liste, puis cliquez sur **rendre actuel**.  
  
3.  Cliquez sur **tester la connexion** pour vérifier que la connexion est disponible.  
  
 Au terme du traitement d'un modèle d'exploration de données, les résultats sont stockés localement et les données ne subissent aucun impact si vous interrompez la connexion à un serveur pour vous connecter à un autre serveur. Cependant, il est recommandé d'éviter de changer les connexions ou de perdre la connexion pendant le traitement d'un modèle d'exploration de données, vous risquez d'endommager les données.  
  
#### <a name="modify-an-existing-server-connection"></a>Modifier une connexion à un serveur existante  
  
1.  Vous ne pouvez pas modifier une connexion existante ; si vous voulez vous connecter à une base de données ou à un serveur différent, vous devez créer une nouvelle connexion.  
  
2.  Si vous devez modifier la chaîne de connexion afin d'augmenter le délai de requête ou ajouter d'autres paramètres spécifiques à l'instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], il est possible de modifier le fichier .dmc où la chaîne de connexion est stockée.  
  
     \<lecteur : > \Users\\< myusername\>\AppData\Local\Microsoft\Data Mining Add-in  
  
##  <a name="bkmk_extconnections"></a> Connexion aux Sources de données externes  
 Tandis que les outils dans le **analyser** ruban fonctionnent exclusivement avec des données dans Excel, les outils dans le **d’exploration de données** ruban permettre de vous connecter directement aux sources de données externes à utiliser en tant qu’entrées pour votre modèle, ou pour échantillonnage.  
  
 Les outils suivants de ces compléments prennent en charge l'utilisation de données externes pour l'exploration de données :  
  
-   [Exemples de données &#40;compléments d’exploration de données SQL Server&#41;](sample-data-sql-server-data-mining-add-ins.md)  
  
-   [Assistant classification &#40;les données des compléments d’exploration de données pour Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Assistant estimation &#40;les données des compléments d’exploration de données pour Excel&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Assistant cluster &#40;les données des compléments d’exploration de données pour Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Assistant prévisions &#40;les données des compléments d’exploration de données pour Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Créer la Structure d’exploration de &#40;compléments d’exploration de données SQL Server&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
-   [Graphique de précision &#40;compléments d’exploration de données SQL Server&#41;](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
-   [Graphique des bénéfices &#40;compléments d’exploration de données SQL Server&#41;](profit-chart-sql-server-data-mining-add-ins.md)  
  
-   [Matrice de classification &#40;compléments d’exploration de données SQL Server&#41;](classification-matrix-sql-server-data-mining-add-ins.md)  
  
### <a name="using-analysis-services-as-a-data-source"></a>Utilisation d'Analysis Services comme source de données  
 Vous ne pouvez pas accéder directement aux données stockées dans un modèle tabulaire ou un cube [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. À la place, créez dans Excel une connexion au serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et utilisez les données pour créer un modèle.  
  
### <a name="relational-data-sources"></a>Sources de données relationnelles  
 Si vous souhaitez utiliser des données d'une source relationnelle comme entrées à votre modèle, vous pouvez vous connecter aux versions suivantes de SQL Server :  
  
-   SQL Server 2008  
  
-   SQL Server 2008 R2  
  
-   SQL Server 2012  
  
 Vous pouvez également obtenir des données de toute autre source de données relationnelle prise en charge comme source de données par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Pour plus d’informations sur les sources de données prises en charge, consultez [des Sources de données dans les modèles multidimensionnels](multidimensional-models/data-sources-in-multidimensional-models.md)  
  
 Notez que les types de données suivants ne peuvent pas être utilisés pour l'exploration de données et généreront une erreur s'ils sont présent lorsque vous créez un modèle :  
  
-   ntext  
  
-   binary  
  
## <a name="see-also"></a>Voir aussi  
 [Trace &#40;Client d’exploration de données pour Excel&#41;](trace-data-mining-client-for-excel.md)  
  
  
