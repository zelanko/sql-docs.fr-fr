---
title: Se connecter aux données sources (client d’exploration de données pour Excel) | Microsoft Docs
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66087099"
---
# <a name="connect-to-source-data-data-mining-client-for-excel"></a>Connexion à une source de données (Client d'exploration de données pour Excel)
  Cette rubrique décrit comment créer et utiliser les connexions utilisées pour stocker des modèles d'exploration de données et pour accéder aux données externes stockées dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 **Connexions d'exploration de données.** La connexion initiale que vous créez lorsque vous lancez les compléments permet d'accéder aux algorithmes, d'analyser les données et de stocker les modèles et structures d'exploration de données.  
  
 Une connexion à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] est nécessaire pour utiliser les outils de modélisation et de visualisation des compléments, car ces derniers dépendent d'algorithmes et de structures de données qui sont fournis par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 **Connexions à des sources de données externes.** Vous pouvez également créer des connexions à des données externes lorsque vous créez des modèles ou enregistrez les résultats. Par exemple, vous pouvez créer un modèle d'exploration de données sur un serveur, puis exécuter une requête de prédiction par rapport au modèle d'exploration de données à l'aide de données stockées dans une autre instance d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], dans un tableau de données Excel, ou dans une source de données externes telle que [!INCLUDE[msCoName](../includes/msconame-md.md)] Access. À chaque fois que vous accédez à une nouvelle source de données, le système vous demande de créer une connexion à l'aide d'une boîte de dialogue.  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq2"></a> Conditions préalables  
 Cette version des compléments nécessite que votre instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] soit SQL Server 2012. Une version séparée des compléments est disponible si vous souhaitez vous connecter à une version antérieure d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Il existe des versions des compléments qui prennent en charge SQL Server 2005, SQL Server 2008 et SQL Server 2008 R2.  
  
 Pour vous connecter à une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], vous devez disposer des autorisations d'accès au serveur de base de données. De plus, les sessions d'exploration de données doivent être activées, et vous devez disposer des autorisations de lecture ou de lecture/écriture sur des objets de base de données stockés sur le serveur.  
  
##  <a name="creating-data-mining-server-connections"></a><a name="bkmk_connect"></a>Création de connexions au serveur d’exploration de données  
 Le groupe **connexions** dans le client d’exploration de données pour Excel et les outils d’analyse de table pour Excel fournit des outils pour gérer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]les connexions à une instance de.  
  
-   Vous pouvez créer la connexion lorsque vous installez le complément, ou vous pouvez ajouter une connexion par la suite.  
  
-   Vous pouvez créer plusieurs connexions et les modifier à tout moment, sauf si vous est en train de créer ou d'interroger un modèle.  
  
     Ne modifiez pas ou ne désactivez pas une connexion lors du traitement d'un modèle d'exploration de données. Le modèle d'exploration de données peut perdre des données ou devenir inutilisable.  
  
-   Une seule connexion peut être active à un moment donné.  
  
### <a name="connections-in-the-excel-add-ins"></a>Connexions dans les compléments Excel  
 Le groupe **connexions** dans le client d’exploration de données pour Excel et les outils d’analyse de table pour Excel est l’emplacement où vous [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]gérez les connexions à une instance de.  
  
##### <a name="create-a-new-server-connection-in-the-excel-add-ins"></a>Créer une nouvelle connexion au serveur dans les compléments Excel  
  
1.  Cliquez sur le bouton **connexion** dans le ruban **analyse** ou **exploration de données** .  
  
    > [!NOTE]  
    >  Le texte du bouton indique si une connexion existe. Quand aucune connexion n’a été établie dans la feuille de calcul, le bouton contient\<le texte « aucune> de connexion ». Si une connexion a été établie auparavant dans la feuille de calcul, le nom de cette connexion s'affiche sur le bouton.  
  
2.  Dans la boîte de dialogue **Analysis Services les connexions** , cliquez sur **nouveau**.  
  
3.  Dans la boîte de dialogue **nouvelle connexion Analysis Services** , tapez le nom du serveur.  
  
4.  Spécifiez la méthode d'authentification.  
  
5.  Sélectionnez une base de données dans la liste déroulante **nom du catalogue** . Si aucune base de données n’existe sur l’instance, sélectionnez **(par défaut)**.  
  
6.  Tapez un nom convivial pour la connexion.  
  
7.  Cliquez sur **tester la connexion** pour vérifier que le serveur et la base de données sont disponibles.  
  
8.  Cliquez sur **OK**, puis sur **Fermer**.  
  
### <a name="connections-using-a-web-service"></a>Connexions à l'aide d'un service Web  
 Si vous utilisez une architecture de client léger pour permettre l’exploration des [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cubes et des données, vous pouvez également configurer une connexion à [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] un serveur via des services Web. Pour obtenir des informations sur la manière de définir un client Web, consultez la documentation en ligne de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Si vous avez accès à un serveur qui a été configuré pour des services Web, vous pouvez spécifier le type de connexion lorsque vous créez celle-ci pour la première fois.  
  
##### <a name="create-an-http-connection-to-analysis-services"></a>Créer une connexion HTTP à Analysis Services  
  
1.  Ouvrez la boîte **de dialogue Nouvelle connexion Analysis Services** .  
  
2.  Pour le nom du serveur, tapez http:// suivi de l'URL affecté au serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
3.  Tapez le nom d'utilisateur et le mot de passe qui sont nécessaires pour accéder au service Web.  
  
### <a name="connections-in-the-visio-add-in"></a>Connexions dans le complément Visio  
 Contrairement à Excel, Visio ne fournit pas un ruban outil et il n'y a pas de boutons destinés à la création ou au contrôle des connexions. En revanche, la connexion de données est créée lorsque vous choisissez une forme d'exploration de données pour la première fois et que vous la déposez sur une page Visio. Un Assistant vous invitera à sélectionner le modèle pour la forme et à définir d'autres options.  
  
 Si vous avez déjà utilisé une connexion à une [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] source de données dans Excel, ces connexions sont répertoriées comme sources de données possibles à partir desquelles sélectionner.  
  
##### <a name="create-a-connection-for-a-visio-shape"></a>Créer une connexion pour une forme Visio  
  
1.  Ouvrez le modèle d'exploration de données et sélectionnez une des formes d'exploration de données.  
  
2.  Effectuez un glisser-déplacer de la forme vers une page vide.  
  
3.  Dans la boîte de dialogue **Sélectionner une source de données** , sélectionnez une source de données dans la liste ou cliquez sur **nouveau**.  
  
4.  Si vous sélectionnez **nouveau**, suivez la procédure décrite précédemment pour spécifier un nom de serveur et de catalogue, ou pour vous connecter par le biais d’un service Web.  
  
##  <a name="changing-connections"></a><a name="bkmk_change"></a>Modification des connexions  
 Vous pouvez créer plusieurs connexions dans la même feuille de calcul mais une seule connexion peut être active à la fois. Le nom de la connexion actuelle est affiché dans le bouton de **connexion** .  
  
 Dans le client d’exploration de données pour Excel, vous pouvez également vérifier la chaîne de connexion et l’état de la connexion actuelle en cliquant sur **trace** , puis sur **connexion actuelle**.  
  
#### <a name="use-a-different-server-connection"></a>Utiliser une connexion différente à un serveur  
  
1.  Cliquez sur **connexion**.  
  
2.  Dans le volet **connexions Analysis Services** , sélectionnez une connexion dans la liste **autres connexions** , puis cliquez sur **mettre en cours**.  
  
3.  Cliquez sur **tester la connexion** pour vérifier que la connexion est disponible.  
  
 Au terme du traitement d'un modèle d'exploration de données, les résultats sont stockés localement et les données ne subissent aucun impact si vous interrompez la connexion à un serveur pour vous connecter à un autre serveur. Cependant, il est recommandé d'éviter de changer les connexions ou de perdre la connexion pendant le traitement d'un modèle d'exploration de données, vous risquez d'endommager les données.  
  
#### <a name="modify-an-existing-server-connection"></a>Modifier une connexion à un serveur existante  
  
1.  Vous ne pouvez pas modifier une connexion existante ; si vous voulez vous connecter à une base de données ou à un serveur différent, vous devez créer une nouvelle connexion.  
  
2.  Si vous devez modifier la chaîne de connexion afin d'augmenter le délai de requête ou ajouter d'autres paramètres spécifiques à l'instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], il est possible de modifier le fichier .dmc où la chaîne de connexion est stockée.  
  
     \<lecteur : > \Utilisateurs\\<le\>complément d’exploration de données myusername \AppData\Local\Microsoft\Data  
  
##  <a name="connecting-to-external-data-sources"></a><a name="bkmk_extconnections"></a>Connexion à des sources de données externes  
 Tandis que les outils du ruban **analyser** fonctionnent exclusivement avec les données dans Excel, les outils du ruban **exploration de données** vous permettent de vous connecter directement à des sources de données externes à utiliser comme entrées pour votre modèle ou pour l’échantillonnage.  
  
 Les outils suivants de ces compléments prennent en charge l'utilisation de données externes pour l'exploration de données :  
  
-   [Exemples de données &#40;SQL Server des compléments d’exploration de données&#41;](sample-data-sql-server-data-mining-add-ins.md)  
  
-   [Assistant classification &#40;compléments d’exploration de données pour Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Assistant estimation &#40;des compléments d’exploration de données pour Excel&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Assistant de cluster &#40;des compléments d’exploration de données pour Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Assistant Prévision &#40;des compléments d’exploration de données pour Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Créer des &#40;de structure d’exploration de données SQL Server des compléments d’exploration de données&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
-   [Graphique d’analyse de précision &#40;SQL Server les compléments d’exploration de données&#41;](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
-   [Graphique des bénéfices &#40;les compléments d’exploration de données SQL Server&#41;](profit-chart-sql-server-data-mining-add-ins.md)  
  
-   [&#40;de matrices de classification SQL Server des compléments d’exploration de données&#41;](classification-matrix-sql-server-data-mining-add-ins.md)  
  
### <a name="using-analysis-services-as-a-data-source"></a>Utilisation d'Analysis Services comme source de données  
 Vous ne pouvez pas accéder directement aux données stockées dans un modèle tabulaire ou un cube [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. À la place, créez dans Excel une connexion au serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et utilisez les données pour créer un modèle.  
  
### <a name="relational-data-sources"></a>Sources de données relationnelles  
 Si vous souhaitez utiliser des données d'une source relationnelle comme entrées à votre modèle, vous pouvez vous connecter aux versions suivantes de SQL Server :  
  
-   SQL Server 2008  
  
-   SQL Server 2008 R2  
  
-   SQL Server 2012  
  
 Vous pouvez également obtenir des données de toute autre source de données relationnelle prise en charge comme source de données par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Pour plus d’informations sur les sources de données prises en charge, consultez [sources de données dans les modèles multidimensionnels](multidimensional-models/data-sources-in-multidimensional-models.md)  
  
 Notez que les types de données suivants ne peuvent pas être utilisés pour l'exploration de données et généreront une erreur s'ils sont présent lorsque vous créez un modèle :  
  
-   ntext  
  
-   binary  
  
## <a name="see-also"></a>Voir aussi  
 [Trace &#40;client d’exploration de données pour Excel&#41;](trace-data-mining-client-for-excel.md)  
  
  
