---
title: Utiliser une connexion de modèle sémantique BI dans Excel ou Reporting Services | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 486195ca-530f-49e8-b40d-0f817db159ee
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 00ee95942a8022ee8d299ab400d36676b51467ab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144174"
---
# <a name="use-a-bi-semantic-model-connection-in-excel-or-reporting-services"></a>Utiliser une connexion de modèle sémantique BI dans Excel ou Reporting Services
  Cette rubrique explique comment utiliser les connexions de modèles sémantiques BI que vous avez créées à l'aide des instructions fournies dans d'autres rubriques. Si vous n’avez pas encore créé un modèle sémantique BI, consultez [créer une connexion de modèle sémantique BI à un classeur PowerPivot](create-a-bi-semantic-model-connection-to-a-power-pivot-workbook.md) et [créer une connexion de modèle sémantique BI vers une base de données Model tabulaires](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md).  
  
##  <a name="bkmk_connect"></a> Se connecter depuis Excel  
 Vous pouvez spécifier une connexion de modèle sémantique BI comme source de données dans Excel ou toute autre application de gestion qui utilise des données de modèle tabulaire Analysis Services. Cette section présente les deux approches de connexion aux données de modèles sémantiques BI à l'aide d'Excel.  
  
 Les connexions de modèles sémantiques BI Excel nécessitent l'installation d'Excel 2010 et du fournisseur OLE DB MSOLAP.5 sur votre station de travail. Des informations supplémentaires sur les exigences de connexion sont fournies plus loin dans cette section.  
  
 **Lancement depuis SharePoint**  
  
-   Cliquez avec le bouton droit sur une connexion de modèle sémantique BI dans une bibliothèque, puis sélectionnez **Lancer Excel**.  
  
 ![Commande de lancement rapide de capture d’écran de BISM](../media/ssas-bism-quicklaunch.gif "commande de lancement rapide de capture d’écran de BISM")  
  
 Cliquez sur **Activer** lorsque vous êtes invité à activer les connexions de données. Excel ouvre un classeur qui contient une liste de champs de tableau croisé dynamique renseignée avec les champs de la source de données sous-jacente.  
  
 **Lancement depuis Excel**  
  
1.  Démarrez Excel et ouvrez un classeur. Sous l'onglet Données, dans le groupe Données externes, cliquez sur **À partir d'autres sources**.  
  
2.  Cliquez sur **À partir d'Analysis Services** et utilisez l'Assistant Connexion de Données pour importer les données.  
  
3.  Entrez l’URL SharePoint du fichier de connexion de modèle sémantique BI (par exemple,  **http://mysharepoint/shared documents/mydata.bism**). Acceptez l'option d'utilisation des informations d'identification de connexion par défaut, **Utiliser l'authentification Windows**. Cliquez sur **Suivant**.  
  
4.  Sur la page suivante, cliquez de nouveau sur **Suivant** . Bien que vous soyez invité à sélectionner une base de données, vous pouvez utiliser uniquement celle spécifiée dans la connexion de modèle sémantique BI.  
  
5.  Dans la dernière page, vous pouvez indiquer un nom convivial et une description. Cliquez sur **Terminer**, puis sur **OK** dans la boîte de dialogue Importer des données, pour importer les données.  
  
 Pour que les connexions réussissent, Excel 2010 et le fichier MSOLAP.5.dll doivent être installés sur l'ordinateur client. Vous pouvez obtenir le fournisseur en installant la version de PowerPivot pour Excel est en cours pour cette version ou vous pouvez télécharger uniquement le fournisseur OLE DB pour Analysis Services à partir de la [page de téléchargement de Feature Pack](http://go.microsoft.com/fwlink/?linkid=214066).  
  
 Pour confirmer que le fichier MSOLAP.5.dll est la version actuelle, vérifiez `HKEY_CLASSES_ROOT\MSOLAP` dans le Registre. `CurVer` doit être défini sur MSOLAP.5.  
  
 Vous devez également disposer des autorisations de lecture sur le fichier de modèle sémantique BI dans SharePoint. Les autorisations de lecture incluent des droits de téléchargement. Excel télécharge les informations de la connexion de modèle sémantique BI depuis SharePoint et ouvre une connexion directe à la base de données via `HTTP Get`. Les demandes de connexion ne sont pas acheminées via SharePoint une fois que les informations de connexion de modèle sémantique BI sont stockées localement.  
  
 Si vous vous connectez à une base de données model tabulaire qui s'exécute sur un serveur Analysis Services, les autorisations SharePoint ne sont pas suffisantes. Vous devez également disposer des autorisations de lecture de base de données sur le serveur. Cette étape doit avoir été effectuée lorsque vous avez créé la connexion de modèle sémantique BI. Pour plus d’informations, consultez [Créer une connexion de modèle sémantique BI à une base de données model tabulaire](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md).  
  
##  <a name="bkmk_use"></a> Se connecter à partir de Reporting Services dans SharePoint  
 Vous pouvez utiliser une connexion de modèle sémantique BI de la même façon que vous utilisez la plupart des sources de données, en spécifiant le fichier comme source de données dans le document ou l'outil qui utilise les données. Bien qu'une connexion de modèle sémantique BI pointe vers une base de données physique sur un autre serveur, vous utilisez le fichier de connexion comme s'il s'agissait de la source de données. L'URL SharePoint de la connexion de modèle sémantique BI est un emplacement de source de données valide pour les rapports [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] qui utilisent des données de modèle sémantique BI.  
  
 Pour la conception de rapports ad hoc dans SharePoint, l'utilisateur qui crée le rapport doit disposer d'autorisations SharePoint sur le fichier de connexion de modèle sémantique BI (.bism) et sur la base de données de modèle sémantique Business Intelligence. Le contexte de sécurité de la connexion est l'utilisateur interactif qui crée le rapport.  
  
  