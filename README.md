# custom_column_Grid
Customization of the Magestore Membership Extension


1.Add this code to Grid.php <br>
<code>
$this->addColumn('member_type', array(
          'header'    => Mage::helper('membership')->__('Member Type'),
          'align'     =>'left',
          'index'     => 'member_type',
		  'width'     => '10px',
      ));
 </code>     
2. Add this code to Form.php <br>
<code>
$fieldset->addField('member_type', 'select', array(
          'label'     => Mage::helper('membership')->__('Member Type'),
          'name'      => 'member_type',
		  'required'  => true,
          'values'    => array(
              array(
                  'value'     => 'buyer',
                  'label'     => Mage::helper('membership')->__('Buyer'),
              ),

              array(
                  'value'     => 'seller',
                  'label'     => Mage::helper('membership')->__('Seller'),
              ),
          ),
      ));
</code>       
3. Run this code to PackageController.php <br>
<code>
$installer = new Mage_Core_Model_Resource_Setup();

$installer->startSetup();

$installer->getConnection()->addColumn($installer->getTable('membership_package'), 'package_type', 'text default NULL');

$installer->endSetup();
</code>
