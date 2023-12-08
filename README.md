# void executors(String username) {
  Handler hand = new Handler(Looper.getMainLooper());
  Thread t = new Thread(new Runnable() {
    Requestsku req = new Requestsku(username);

    @Override
    public void run() {
      synchronized (this) {
        req.init();
      }

      // TODO: Implement this method
      hand.post(new Runnable() {
        @Override
        public void run() {
          lprofilinfo.add(req.getResult());
          adapter.notifyDataSetChanged();
        }
      });
    }
  });
  t.start();
}
