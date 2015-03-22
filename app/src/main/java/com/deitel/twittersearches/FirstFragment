package com.deitel.twittersearches;

/**
 * Created by lcy on 2015/3/22.
 */
        import android.app.Activity;
        import android.app.ListFragment;
        import android.os.Bundle;
        import android.support.v4.app.Fragment;
        import android.view.LayoutInflater;
        import android.view.View;
        import android.view.ViewGroup;
        import android.widget.ListAdapter;
        import android.widget.ListView;
        import android.widget.TextView;

public class FirstFragment extends ListFragment {
    // the fragment initialization parameters, e.g. ARG_ITEM_NUMBER
    private static final String ARG_PARAM1 = "query";
    private static final String ARG_PARAM2 = "tag";

    private String query;
    private String tag;

    private OnFragmentInteractionListener mListener;

    private ListView mListView;
    private ListAdapter mAdapter;

    public static FirstFragment newInstance(String query, String tag) {
        FirstFragment fragment = new FirstFragment();
        Bundle args = new Bundle();
        args.putString(ARG_PARAM1, query);
        args.putString(ARG_PARAM2, tag);
        fragment.setArguments(args);
        return fragment;
    }

    public FirstFragment() {
        // Required empty public constructor
    }

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        if (getArguments() != null) {
            query = getArguments().getString(ARG_PARAM1);
            tag = getArguments().getString(ARG_PARAM2);
        }
        mAdapter = ((MainActivity)getActivity()).getAdapter();
    }

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        View myView = inflater.inflate(R.layout.fragment_first, container, false);
        mListView = (ListView) myView.findViewById(android.R.id.list);
        mListView.setAdapter(mAdapter);
        mListView.setOnItemLongClickListener(((MainActivity)getActivity()).getOnItemLongClickListener());

        return myView;
    }

    @Override
    public void onAttach(Activity activity) {
        super.onAttach(activity);
        try {
            mListener = (OnFragmentInteractionListener) activity;
        } catch (ClassCastException e) {
            throw new ClassCastException(activity.toString()
                    + " must implement OnFragmentInteractionListener");
        }
    }

    @Override
    public void onDetach() {
        super.onDetach();
        mListener = null;
    }

    @Override
    public void onListItemClick(ListView L,View v,int position,long id){
        if (mListener!=null){
            // Notify the active callbacks interface (the activity, if the
            // fragment is attached to one) that an item has been selected.
            String query2 = ((TextView) v).getText().toString();
            mListener.sendToSecondFrag(query2);
        }
    }

    public void setEmptyText(CharSequence emptyText) {
        View emptyView = mListView.getEmptyView();
        if (emptyView instanceof TextView) {
            ((TextView) emptyView).setText(emptyText);
        }
    }

    public interface OnFragmentInteractionListener {
        public void sendToSecondFrag(String query);
    }

