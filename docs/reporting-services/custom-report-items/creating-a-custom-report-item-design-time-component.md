---
title: "Création d’un composant de conception de rapport personnalisé élément | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom report items, creating
ms.assetid: 323fd58a-a462-4c48-b188-77ebc0b4212e
caps.latest.revision: 37
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 2cb994a0cb4dde6b6ea5f671238272e574e7721b
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="creating-a-custom-report-item-design-time-component"></a>Création d'un composant au moment de la conception d'élément de rapport personnalisé
  Un composant au moment de la conception d'élément de rapport personnalisé est un contrôle qui peut être utilisé dans l'environnement du Concepteur de rapports Visual Studio. Le composant au moment de la conception d'élément de rapport personnalisé fournit une aire de conception activée qui prend en charge les opérations de glisser-déplacer et l'intégration avec l'Explorateur de propriétés [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], tout en fournissant des éditeurs de propriété personnalisée.  
  
 Avec un composant au moment de la conception d'élément de rapport personnalisé, l'utilisateur peut positionner un élément de rapport personnalisé sur un rapport dans l'environnement de conception, définir des propriétés de données personnalisées sur l'élément de rapport personnalisé, puis enregistrer cet élément en tant que partie du projet de rapport.  
  
 Les propriétés définies à l'aide du composant au moment de la conception dans l'environnement de développement sont sérialisées et désérialisées par l'environnement de conception hôte, puis stockées comme éléments dans le fichier RDL (Report Definition Language). Lorsque le rapport est exécuté par le processeur de rapports, les propriétés définies à l'aide du composant au moment de la conception sont passées par le processeur de rapports à un composant d'exécution d'élément de rapport personnalisé, qui génère l'élément de rapport personnalisé et le repasse au processeur de rapports.  
  
> [!NOTE]  
>  Le composant au moment du design article de rapport personnalisé est implémenté comme un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] composant. Ce document décrit les détails d'implémentation spécifiques au composant au moment de la conception d'élément de rapport personnalisé. Pour plus d’informations sur le développement de composants à l’aide de la [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], consultez [composants dans Visual Studio](http://go.microsoft.com/fwlink/?LinkId=116576) dans MSDN library.  
  
 Pour voir un exemple d’un élément de rapport personnalisé totalement implémenté, [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="implementing-a-design-time-component"></a>Implémentation d'un composant au moment de la conception  
 La classe principale d’un composant au moment du design d’élément rapport personnalisé est héritée de la **Microsoft.ReportDesigner.CustomReportItemDesigner** classe. Outre les attributs standards utilisés pour un [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] contrôle, votre classe de composant doit définir un **CustomReportItem** attribut. Cet attribut doit correspondre au nom de l'élément de rapport personnalisé tel que défini dans le fichier reportserver.config. Pour obtenir une liste des attributs [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], consultez la section Attributs dans la documentation du SDK du [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
 L'exemple de code suivant illustre l'application d'attributs à un contrôle au moment de la conception d'élément de rapport personnalisé :  
  
```csharp  
namespace PolygonsCRI  
{  
    [LocalizedName("Polygons")]  
    [Editor(typeof(CustomEditor), typeof(ComponentEditor))]  
        [ToolboxBitmap(typeof(PolygonsDesigner),"Polygons.ico")]  
        [CustomReportItem("Polygons")]  
  
    public class PolygonsDesigner : CustomReportItemDesigner  
    {  
...  
```  
  
### <a name="initializing-the-component"></a>Initialisation du composant  
 Pour passer des propriétés spécifiées par l'utilisateur pour un élément de rapport personnalisé, une classe <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> doit être utilisée. Votre implémentation de la **CustomReportItemDesigner** classe doit substituer la **InitializeNewComponent** méthode pour créer une nouvelle instance de votre composant <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> classe et définir les valeurs par défaut.  
  
 L’exemple de code suivant montre un exemple d’une substitution de classe rapport personnalisé élément composant de conception du **CustomReportItemDesigner.InitializeNewComponent** méthode d’initialisation du composant <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> classe :  
  
```csharp  
public override void InitializeNewComponent()  
        {  
            CustomData = new CustomData();  
            CustomData.DataRowHierarchy = new DataHierarchy();  
  
            // Shape grouping  
            CustomData.DataRowHierarchy.DataMembers.Add(new DataMember());  
            CustomData.DataRowHierarchy.DataMembers[0].Group = new Group();  
            CustomData.DataRowHierarchy.DataMembers[0].Group.Name = Name + "_Shape";  
            CustomData.DataRowHierarchy.DataMembers[0].Group.GroupExpressions.Add(new ReportExpression());  
  
            // Point grouping  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers.Add(new DataMember());  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group = new Group();  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group.Name = Name + "_Point";  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group.GroupExpressions.Add(new ReportExpression());  
  
            // Static column  
            CustomData.DataColumnHierarchy = new DataHierarchy();  
            CustomData.DataColumnHierarchy.DataMembers.Add(new DataMember());  
  
            // Points  
            IList<IList<DataValue>> dataValues = new List<IList<DataValue>>();  
            CustomData.DataRows.Add(dataValues);  
            CustomData.DataRows[0].Add(new List<DataValue>());  
            CustomData.DataRows[0][0].Add(NewDataValue("X", ""));  
            CustomData.DataRows[0][0].Add(NewDataValue("Y", ""));  
        }  
```  
  
### <a name="modifying-component-properties"></a>Modification des propriétés du composant  
 Vous pouvez modifier **CustomData** propriétés dans l’environnement de conception de plusieurs façons. Vous pouvez modifier toute propriété exposée par le composant au moment de la conception et marquée avec l'attribut <xref:System.ComponentModel.BrowsableAttribute>, à l'aide de l'Explorateur de propriétés [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. En outre, vous pouvez modifier les propriétés en faisant glisser des éléments sur l’aire de conception de l’élément de rapport personnalisé, ou en cliquant sur le contrôle dans l’environnement de conception et en sélectionnant **propriétés** dans le menu contextuel pour afficher une fenêtre de propriétés personnalisées.  
  
 Le code suivant montre d’exemple un **Microsoft.ReportDesigner.CustomReportItemDesigner.CustomData** propriété qui a le <xref:System.ComponentModel.BrowsableAttribute> attribut appliqué :  
  
```csharp  
[Browsable(true), Category("Data")]  
public string DataSetName  
{  
      get  
      {  
         return CustomData.DataSetName;  
      }  
      set  
      {  
         CustomData.DataSetName = value;  
      }  
   }  
  
```  
  
 Vous pouvez fournir votre composant au moment de la conception avec une boîte de dialogue d'éditeur de propriétés personnalisées. L'implémentation d'éditeur de propriétés personnalisées doit hériter de la classe <xref:System.ComponentModel.ComponentEditor> et doit créer une instance d'une boîte de dialogue destinée à l'édition de propriétés.  
  
 L'exemple suivant montre l'implémentation d'une classe qui hérite de <xref:System.ComponentModel.ComponentEditor> et ouvre une boîte de dialogue d'éditeur de propriétés personnalisées :  
  
```csharp  
internal sealed class CustomEditor : ComponentEditor  
{  
   public override bool EditComponent(  
      ITypeDescriptorContext context, object component)  
    {  
     PolygonsDesigner designer = (PolygonsDesigner)component;  
     PolygonProperties dialog = new PolygonProperties();  
     dialog.m_designerComponent = designer;  
     DialogResult result = dialog.ShowDialog();  
     if (result == DialogResult.OK)  
     {  
        designer.Invalidate();  
        designer.ChangeService().OnComponentChanged(designer, null, null, null);  
        return true;  
     }  
     else  
        return false;  
    }  
}  
```  
  
 Votre boîte de dialogue d'éditeur de propriétés personnalisées peut appeler l'Éditeur d'expressions du Concepteur de rapports. Dans l'exemple suivant, l'Éditeur d'expressions est appelé lorsque l'utilisateur sélectionne le premier élément dans la zone de liste déroulante :  
  
```csharp  
private void EditableCombo_SelectedIndexChanged(object sender,   
    EventArgs e)  
{  
   ComboBox combo = (ComboBox)sender;  
   if (combo.SelectedIndex == 0 && m_launchEditor)  
   {  
      m_launchEditor = false;  
      ExpressionEditor editor = new ExpressionEditor();  
      string newValue;  
      newValue = (string)editor.EditValue(null, m_designerComponent.Site, m_oldComboValue);  
      combo.Items[0] = newValue;  
   }  
}  
  
```  
  
### <a name="using-designer-verbs"></a>Utilisation des verbes de concepteur  
 Un verbe de concepteur est une commande de menu liée à un gestionnaire d'événements. Vous pouvez ajouter des verbes de concepteur qui apparaîtront dans le menu contextuel d'un composant lorsque votre contrôle au moment de l'exécution d'élément de rapport personnalisé est utilisé dans l'environnement de conception. Vous pouvez retourner la liste des verbes de concepteur disponibles à partir de votre composant d’exécution à l’aide de la **verbes** propriété.  
  
 L'exemple de code suivant illustre l'ajout d'un verbe de concepteur et d'un gestionnaire d'événements au <xref:System.ComponentModel.Design.DesignerVerbCollection>, ainsi que le code du gestionnaire d'événements :  
  
```csharp  
public override DesignerVerbCollection Verbs  
{  
    get  
    {  
        if (m_verbs == null)  
        {  
            m_verbs = new DesignerVerbCollection();  
            m_verbs.Add(new DesignerVerb("Proportional Scaling", new EventHandler(OnProportionalScaling)));  
         m_verbs[0].Checked = (GetCustomProperty("poly:Proportional") == bool.TrueString);  
        }  
  
        return m_verbs;  
    }  
}  
  
private void OnProportionalScaling(object sender, EventArgs e)  
{  
   bool proportional = !  
        (GetCustomProperty("poly:Proportional") == bool.TrueString);  
   m_verbs[0].Checked = proportional;  
   SetCustomProperty("poly:Proportional", proportional.ToString());  
   ChangeService().OnComponentChanged(this, null, null, null);  
   Invalidate();  
}  
```  
  
### <a name="using-adornments"></a>Utilisation d'ornements  
 Classes d’éléments de rapport personnalisés peuvent également implémenter un **Microsoft.ReportDesigner.Design.Adornment** classe. Un ornement permet au contrôle d'élément de rapport personnalisé de fournir des zones à l'extérieur du rectangle principal de l'aire de conception. Ces zones permettent de gérer les événements de l'interface utilisateur, tels que les clics de souris et les opérations de glisser-déplacer. Le **ornement** classe qui est définie dans le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **Microsoft.ReportDesigner** espace de noms est une implémentation directe de la <xref:System.Windows.Forms.Design.Behavior.Adorner> classe trouvé dans les Windows Forms. Pour obtenir une documentation complète sur le **ornement** de classe, consultez [vue d’ensemble du Service de comportement](http://go.microsoft.com/fwlink/?LinkId=116673) dans MSDN library. Pour un exemple de code qui implémente un **Microsoft.ReportDesigner.Design.Adornment** de classe, consultez [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
 Pour plus d'informations sur la programmation et l'utilisation de Windows Forms dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], consultez les rubriques suivantes dans MSDN Library :  
  
-   Attributs au moment de la conception pour les composants  
  
-   Composants dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]  
  
-   Procédure pas à pas : création d'un contrôle Windows Forms qui tire parti des fonctionnalités au moment de la conception de Visual Studio  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture d’élément de rapport personnalisé](../../reporting-services/custom-report-items/custom-report-item-architecture.md)   
 [Création d’un composant d’exécution de rapport personnalisé élément](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Bibliothèques de classes élément de rapport personnalisé](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)   
 [Comment : déployer un élément de rapport personnalisé](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
