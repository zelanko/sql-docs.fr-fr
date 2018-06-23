---
title: Activer et désactiver l’impression côté client pour Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e709c96-7517-4547-8ef6-5632f8118524
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 9b5c7c1d879b2ffc9cb333bed193af9239996536
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141961"
---
# <a name="enable-and-disable-client-side-printing-for-reporting-services"></a>Activer et désactiver l'impression côté client pour Reporting Services
  Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] contrôle ActiveX, **RSClientPrint**, permet une impression côté client pour les rapports affichés dans un navigateur. Le contrôle affiche une boîte de dialogue d'impression personnalisée qui prend en charge des fonctionnalités communes à d'autres boîtes de dialogue d'impression. Les fonctionnalités incluent l'aperçu avant impression, les sélections de page pour spécifier des pages et des plages spécifiques, les marges des pages, et l'orientation. Bien que l'impression côté client soit activée par défaut, vous pouvez désactiver cette fonctionnalité pour l'empêcher d'être utilisée.  
  
> [!NOTE]  
>  Des autorisations d'administrateur sont nécessaires pour le téléchargement des contrôles ActiveX.  
  
## <a name="downloading-the-activex-control"></a>Téléchargement du contrôle ActiveX  
 Chaque utilisateur souhaitant utiliser la fonctionnalité d'impression doit télécharger et installer le contrôle ActiveX qui permet l'impression côté client. La première fois qu’un utilisateur clique sur le **imprimante** icône sur la barre d’outils rapport, le contrôle est téléchargé sur l’ordinateur Microsoft ActiveX. Une fois que le contrôle est téléchargé, la **impression** boîte de dialogue affiche chaque fois que l’utilisateur clique sur le **imprimante** icône.  
  
 En fonction des paramètres du navigateur, l'installation du contrôle peut être demandée à l'utilisateur, être bloquée ou s'effectuer de manière transparente en arrière-plan.  
  
 Pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer, les paramètres qui affectent le téléchargement du contrôle ActiveX et l’installation sont spécifiés via le **ActiveX plug-ins et les contrôles** nœud dans le **paramètres de sécurité** page la zone de contenu Web. Les paramètres suivants déterminent si les utilisateurs peuvent télécharger et exécuter le contrôle d'impression, en fonction des spécifications de sécurité de la zone Web :  
  
-   Télécharger les contrôles ActiveX signés.  
  
-   Contrôles ActiveX reconnus sûrs pour l'écriture de scripts.  
  
-   Exécuter les contrôles ActiveX et les plug-ins.  
  
 Les utilisateurs qui souhaitent utiliser **RSClientPrint** pour effectuer l’impression côté client doive activer ce qui suit :  
  
-   **Télécharger les contrôles ActiveX signés** et **contrôle de Script ActiveX reconnus sûr pour l’écriture de scripts** pour l’installation.  
  
-   **Exécuter les contrôles ActiveX et plug-ins** pour les opérations d’impression en cours.  
  
 Le **RSClientPrint** contrôle ActiveX est signé, ce qui signifie qu’il contient un certificat numérique valide à partir de [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
## <a name="enabling-and-disabling-client-side-printing"></a>Activation et désactivation de l'impression côté client  
 Les administrateurs de serveur de rapports ont la possibilité de désactiver la fonctionnalité d’impression en définissant la propriété de système de serveur de rapports **EnableClientPrinting** à `false`. Cela entraîne la désactivation de l'impression côté client pour tous les rapports gérés par ce serveur. Par défaut, **EnableClientPrinting** a la valeur `true`. Vous pouvez désactiver l'impression côté client de différentes façons :  
  
-   Pour un **serveur de rapports en mode natif**:  
  
    1.  Lancez [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] avec des privilèges d'administrateur.  
  
    2.  Connectez-vous à une instance de serveur de rapports dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
    3.  Cliquez avec le bouton droit sur le nœud du serveur de rapports et sélectionnez **Propriétés**. Si l'option **Propriétés** est désactivée, vérifiez que vous avez lancé [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] avec des privilèges d'administrateur.  
  
    4.  Sélectionnez **activer le téléchargement pour le contrôle d’impression client ActiveX**.  
  
    5.  Cliquez sur **OK**.  
  
-   Pour un **serveur de rapports en mode SharePoint**:  
  
    1.  Dans l'Administration centrale de SharePoint, cliquez sur **Gestion des applications**.  
  
    2.  Cliquez sur **Gérer les applications de service**.  
  
    3.  Cliquez sur le nom de votre application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et cliquez sur **Gérer** dans le ruban SharePoint.  
  
    4.  Cliquez sur **Paramètres système**.  
  
    5.  Sélectionnez **Activer l'impression cliente**. L'option **Activer l'impression cliente** se trouve en bas de la page.  
  
    6.  Cliquez sur **OK**.  
  
-   Écrire du code pour définir la propriété de système de serveur de rapports ou script **EnableClientPrinting** à `false.`  
  
 L'exemple de script suivant illustre une approche possible en matière de désactivation de l'impression côté client. Compilez et exécutez le code [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] suivant afin d'affecter à la propriété **EnableClientPrinting** la valeur **False**. Une fois le code exécuté, redémarrez les services Internet (IIS).  
  
### <a name="sample-script"></a>Exemple de script  
  
```  
Imports System  
Imports System.Web.Services.Protocols  
Class Sample  
   Public Shared Sub Main()  
Dim rs As New ReportingService()  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
        Dim props(0) As [Property]  
        Dim setProp As New [Property]  
        setProp.Name = "EnableClientPrinting"  
        setProp.Value = “False”   
        props(0) = setProp  
        Try  
            rs.SetSystemProperties(props)  
        Catch ex As System.Web.Services.Protocols.SoapException  
            Console.Write(ex.Detail.InnerXml)  
        Catch e as Exception  
            Console.Write(e.Message)  
        End Try  
    End Sub 'Main  
End Class 'Sample  
```  
  
  