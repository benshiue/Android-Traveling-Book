# 使用 FragmentPagerAdapter


* MainActivity.java

```java
import android.app.Activity;
import android.app.Fragment;
import android.os.Bundle;
import android.support.annotation.Nullable;
import android.support.v13.app.FragmentPagerAdapter;
import android.support.v4.view.ViewPager;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.TextView;

public class MainActivity extends Activity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        
        // 建立 ViewPager 元件。
        ViewPager pager = new ViewPager(this);
        // 需提供 ID，否則會拋出錯誤。
        pager.setId(View.generateViewId());
        // FragmentPagerAdapter 會保留每個顯示的 Fragment 狀態，記憶體不會釋放。
        // 這裡只先提供基本可以運作的寫法，特性再後面章節介紹。
        pager.setAdapter(new FragmentPagerAdapter(getFragmentManager()) {

            @Override
            public Fragment getItem(int position) {
                // 提供 Fragment
                return new MainFragment();
            }

            @Override
            public int getCount() {
                // 提供頁數
                return 5;
            }
        });
        setContentView(pager);
    }

    public static class MainFragment extends Fragment {
        @Nullable
        @Override
        public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
            // 設定 Fragment 內容
            TextView view = new TextView(getActivity());
            view.setText("Fragment Text");
            return view;
        }
    }
}
```

