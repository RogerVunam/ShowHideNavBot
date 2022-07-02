# ShowHideNavBot

 
# Step1 : Vì Fragment đang nằm trong MainActivity nên là để sử dụng navBot từ Activity sẽ dùng requireActivity
```
val navBot = requireActivity()!!.findViewById<BottomNavigationView>(R.id.navBot)
```

# Step2 : Viết 1 fun để check nếu mà true thì là fragment đó đang được nạp vào ngược lại thì phá huỷ 
```
private fun checkComeIn(isComeIn:Boolean){
        if (isComeIn){
            val navBot = requireActivity()!!.findViewById<BottomNavigationView>(R.id.navBot)
            navBot.visibility = View.GONE -> nạp vào thì giấu navBot đi
        }else{
            val navBot = requireActivity()!!.findViewById<BottomNavigationView>(R.id.navBot)
            navBot.visibility = View.VISIBLE -> còn qua fragment khác thì hiện nó lại
        }
    }
```


# Step3 : Viết fun checkComeIn ở nơi nạp vào và nơi phá huỷ 
```
override fun onCreateView(
        inflater: LayoutInflater, container: ViewGroup?,
        savedInstanceState: Bundle?
    ): View? {
        binding = FragmentSettingAndPrivacyBinding.inflate(layoutInflater) 
        checkComeIn(true)
        return binding.root
    }
```  

```
 override fun onDestroy() {
        super.onDestroy()
        binding == null
        checkComeIn(false)
    }
```    
