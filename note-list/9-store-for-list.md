
# กำหนด Note List ให้ใช้ข้อมูลจาก Store มาแสดง

```js

// app/desktop/src/view/notelist/NotelistView.js

Ext.define('CounterApp.view.notelist.NotelistView',{
	xtype: 'notelistview',
	cls: 'notelistview',
	controller: {type: 'notelistviewcontroller'},
	viewModel: {type: 'notelistviewmodel'},
	requires: [],
	extend: 'Ext.Container',

    // กำหนดให้ Container scroll ได้ ถ้า child component ด้านใน มีขนาดเกินพื้นที่
	scrollable: true,
	items: [
		{
			xtype: 'list',
			itemTpl: '{message}',

            // สลับจาก data property มาใช้ store property แทน
			store: {
                // เรียกใช้ storeId
				type: 'notes'
			},
		}
	]
});

```

บันทึกและทดสอบผล